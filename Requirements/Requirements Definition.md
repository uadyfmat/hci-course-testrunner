# Requirements Definition

## Content

- [Functional Requirements](#functional-requirements)
- [Non-Functional Requirements](#non-functional-requirements)
- [Metrics Related to Non-Functional Requirements](#metrics-related-to-non-functional-requirements)

## Description
This section is intended to specify the functional requirements of the system to be developed during the period January-May 2024. In previous phases of the project, it was determined that the way to mitigate the usability problems present in the *Test-Runner* system and its currently established form of use, is through an extension of Visual Studio Code, which allows users to use the tool locally. 

## Abbreviations
- **OS:** Operating System
- **VSCode:** Visual Studio Code
- **FR:** Functional Requirement
- **NFR:** Non-Functional Requirement

## Functional Requirements

### FR 1

---

**Name:** *Detect automatically the user's OS*

**Description:** The system should be able to detect the user's OS without the user having to specify it, in order to install dependencies and configure environment variables. 

**Priority:** Low

**Conditions:** This requirement arises from [Functional Requirement 2](#fr-2) and [Functional Requirement 3](#fr-3), and from [Non-Functional Requirement 1](#nfr-1). The validity of this requirement is determined by the requirements mentioned above.

>  **Note:** For understanding the user interaction with this requirement, see the *Normal Flow* and *Alternative Flow* sections for the [FR2](#fr-2) or [FR3](#fr-3).


### FR 2

---

**Name:** *Install required dependencies*

**Description:** The system must have the option to install the required dependencies the first time the extension is configured. The user will be able to decide if they wants certain dependencies to be installed and select them manually (in case the user already has some dependencies installed), or if they wants to skip this option.

**Priority:** Low

**Conditions:** The user will choose whether to install the dependencies of their choice or not to install anything additional.

> **Note:** This requirement depends on [RF1](#fr-1).

**Normal Flow:** 

1. The user installs the extension.

2. The user specifies the dependencies to install.

3. The system automatically detects your OS (Depending on the OS, a specific dependency manager is used).

4. The system installs the specified dependencies.

**Alternative Flow:** 

1. The user has previously installed the required dependencies.

2. The user installs the extension.

3. The user omits the installation of dependencies through the extension.

### FR 3

---

**Name:** *Add installation paths to OS environment variables*

**Description:** The system must be able to add the installation path of the dependencies to the OS environment variables.

**Priority:** Low

**Conditions:** the user has previously selected the desired dependencies for installation through the system.

> **Note:** This requirement depends on [RF1](#fr-1) and [RF2](#fr-2).

**Normal Flow:** 

1. The system automatically detects your OS.

2. The system installs the specified dependencies.

3. The system adds the dependencies installation paths to the OS environment variables.

> **Note:** Depending of the OS, the command to add installation paths to the environment variables changes.

**Alternative Flow:** 

1. The user omits the installation of dependencies through the extension.


### FR 4

---

**Name:** *Install Test-Runner*

**Description:** El sistema deberá ser capaz de instalar la herramienta Test-Runner a través del gestor de dependencias *npm*.

**Priority:** High

**Conditions:** El sistema validará si ya se tiene instalada la herramienta Test-Runner antes de volver a intentar instalarla.

**Normal Flow:** 

1. El usuario selecciona la opción para instalar la herramienta Test-Runner.

2. El sistema valida si se tiene ya una instalación de Test-Runner en el sistema.

3. La validación determina que no se poseen instalaciones previas de la herramienta.

4. El sistema instala la herramienta Test-Runner.

**Alternative Flow:** 

1. El usuario selecciona la opción para instalar la herramienta Test-Runner.

2. El sistema valida si se tiene ya una instalación de Test-Runner en el sistema.

3. La validación determina que ya se tiene instalada la herramienta Test-Runner en el sistema.

4. El sistema alerta al usuario sobre la instalación presente.

5. El sistema detiene el proceso de instalación.

### FR 5

---

**Name:** *Show Test-Runner detail's tab*

**Description:** El sistema deberá mostrar una pestaña que describa el funcionamiento de la extensión, así como los comandos que puede utilizar el usuario para interactuar con ella, y los apartados nuevos que agrega la extensión.

**Priority:** Medium

**Conditions:** La pestaña aparecerá la primera vez que se instala la extensión, o si el usuario ingresa el comando de *Ayuda*.

**Normal Flow 1:** 

1. El usuario instala la extensión.

2. La extensión muestra la pestaña de detalles.

**Normal Flow 2:** 

1. El usuario ingresa el comando de *Ayuda*.

2. La extensión muestra la pestaña de detalles.

### FR 6

---

**Name:** *Show individual test status*

**Description:** El sistema deberá mostrar, para cada prueba presente en la carpeta del repositorio de forma individual, si ya ha sido ejecutada y ha pasado la prueba, o si por el contrario no ha pasado la prueba.

**Priority:** Medium

**Conditions:** Los flujos que se presentan a continuación suponen que la carpeta abierta al momento de realizar las acciones corresponde al de una estructura de repositorio correcta para el uso de la herramienta Test-Runner.

**Normal Flow:** 

1. El usuario ha ejecutado la prueba individual.

2. La prueba ha pasado.

3. El sistema muestra, para la prueba individual, el estado de *Pasado* de la prueba.

**Alternative Flow:** 

1. El usuario ha ejecutado la prueba individual.

2. La prueba no ha pasado.

3. El sistema muestra, para la prueba individual, el estado de *No Pasado* de la prueba.

### FR 7

---

**Name:** *Show tests batch status*

**Description:** El sistema deberá mostrar, al nivel de la carpeta del repositorio, si todas las pruebas han sido ejecutadas y han pasado, o si por el contrario no han pasado todas las pruebas.

**Priority:** Medium

**Conditions:** Los flujos que se presentan a continuación suponen que la carpeta abierta al momento de realizar las acciones corresponde al de una estructura de repositorio correcta para el uso de la herramienta Test-Runner.

**Normal Flow:** 

1. El usuario ejecuta todas las pruebas.

2. Todas las pruebas han pasado.

3. El sistema muestra el estado de *Pasado* de las pruebas del repositorio.

**Alternative Flow:** 

1. El usuario ejecuta todas las pruebas.

2. No todas las pruebas han pasado.

3. El sistema muestra el estado de *No Pasado* de las pruebas del repositorio.

### FR 8

---

**Name:** *Execute individual test*

**Description:** El sistema deberá ser capaz de ejecutar cada una de las pruebas de forma individual.

**Priority:** High

**Conditions:** Los flujos que se presentan a continuación suponen que la carpeta abierta al momento de realizar las acciones corresponde al de una estructura de repositorio correcta para el uso de la herramienta Test-Runner.

**Normal Flow:**

1. El usuario pulsa el botón / ingresa el comando para ejecutar una prueba.

2. El sistema ejecuta la prueba seleccionada.

3. El sistema actualiza el estado de la prueba.

### FR 9

---

**Name:** *Execute tests batch*

**Description:** El sistema deberá ser capaz de ejecutar por lotes todas las pruebas de la carpeta del repositorio.

**Priority:** High

**Conditions:** Los flujos que se presentan a continuación suponen que la carpeta abierta al momento de realizar las acciones corresponde al de una estructura de repositorio correcta para el uso de la herramienta Test-Runner.

**Normal Flow:** 

1. El usuario pulsa el botón / ingresa el comando para ejecutar todas las pruebas.

2. El sistema ejecuta cada prueba de forma individual.

3. El sistema actualiza el estado de las pruebas al nivel de la carpeta del repositorio.

### FR 10

---

**Name:** *Stop tests execution*

**Description:** Durante la ejecución de las pruebas, el sistema deberá tener la opción de detener al momento la ejecución de la prueba.

**Priority:** Medium

**Conditions:** Los flujos que se presentan a continuación suponen que la carpeta abierta al momento de realizar las acciones corresponde al de una estructura de repositorio correcta para el uso de la herramienta Test-Runner.

**Normal Flow:** 

1. El usuario pulsa el botón / ingresa el comando para ejecutar una prueba.

2. El sistema ejecuta la prueba seleccionada.

3. Antes de finalizar la prueba, el usuario pulsa el botón / ingresa el comando para detener la prueba.

4. El sistema detiene la ejecución de la prueba.

### FR 11

---

**Name:** *Show tests result*

**Description:** El sistema deberá ser capaz de mostrar la ejecución de las pruebas realizadas, a partir de la salida devuelta por la herramienta Test-Runner

**Priority:** Medium

**Conditions:** None.

**Normal Flow:** 

1. El usuario pulsa el botón / ingresa el comando para ejecutar una prueba.

2. El sistema ejecuta la prueba seleccionada.

3. Se determina si la prueba ha pasado o no.

4. El sistema muestra al usuario el resultado de la prueba.

### FR 12

---

**Name:** *Update individual test status*

**Description:** El sistema deberá actualizar el estado de una prueba de forma individual una vez que haya sido ejecutada.

**Priority:** Medium

**Conditions:** Los flujos que se presentan a continuación suponen que la carpeta abierta al momento de realizar las acciones corresponde al de una estructura de repositorio correcta para el uso de la herramienta Test-Runner.

**Normal Flow:** 

1. El usuario pulsa el botón / ingresa el comando para ejecutar una prueba individual.

2. El sistema ejecuta la prueba seleccionada.

3. La prueba ha pasado.

4. El sistema le muestra el resultado de la ejecución al usuario.

5. El sistema actualiza el estado de la prueba individual a *Pasado*.

**Alternative Flow:** 

1. El usuario pulsa el botón / ingresa el comando para ejecutar una prueba individual.

2. El sistema ejecuta la prueba seleccionada.

3. La prueba no ha pasado.

4. El sistema le muestra el resultado de la ejecución al usuario.

5. El sistema actualiza el estado de la prueba individual a *No Pasado*.

### FR 13

---

**Name:** *Update tests batch status*

**Description:** El sistema deberá actualizar el estado de las pruebas a nivel de la carpeta del repositorio una vez hayan sido ejecutadas.

**Priority:** Medium 

**Conditions:** Los flujos que se presentan a continuación suponen que la carpeta abierta al momento de realizar las acciones corresponde al de una estructura de repositorio correcta para el uso de la herramienta Test-Runner.

**Normal Flow:** 

1. El usuario pulsa el botón / ingresa el comando para ejecutar todas las pruebas de forma individual.

2. El sistema ejecuta todas las pruebas.

3. Todas las pruebas han pasado.

4. El sistema le muestra el resultado de la ejecución al usuario.

5. El sistema actualiza el estado de las pruebas al nivel de la carpeta del repositorio a *Pasado*.

**Alternative Flow:** 

1. El usuario pulsa el botón / ingresa el comando para ejecutar todas las pruebas de forma individual.

2. El sistema ejecuta todas las pruebas.

3. No odas las pruebas han pasado.

4. El sistema le muestra el resultado de la ejecución al usuario.

5. El sistema actualiza el estado de las pruebas al nivel de la carpeta del repositorio a *No Pasado*.

## Non-Functional Requirements

### NFR 1

---

**Name:** *Compatibility with differents OS*

**Description:** The system must be compatible with OS that are compatible with VSCode, such as Windows, macOS and Linux.

**Priority:** High

**Quality Attribute Related:** wasd

**Metric Related:** [wasd](#)

### NFR 2

---

**Name:** *Ease of configuration*

**Description:** The system should provide clear and simple instructions for installation and initial configuration.

**Priority:** High

**Quality Attribute Related:** wasd

**Metric Related:** [wasd](#)

## Metrics Related to Non-Functional Requirements

### Metric 1

---

**Name:** 

**Description:** 

**Usage:** 

### Metric 2

---