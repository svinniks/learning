# Gradle

- **Ant** does have core support for dependency management! (Ivy is a library for ant which does that?)
- **Maven** has convention (convention over configuration) like folder structure.
- **Gradle** uses Groovy and/or Kotlin for configuration (DSL)

# Dependencies

- **Repositories** contain dependencies. Gradle can use Maven repos (central, local) and even the File System.
- Gradle will pull deps and store them in it's own cache.
- Gradle has more funcionality of how deps are being pulled
- Gradle allows **custom dependency scopes** (unlike Maven, which has only the predefined scopes)

# Incremental builds

- Build cache
- Daemon process - keeps running in memory and has all build info in memory

# Plugins

# DSL

build.gradle written with Groovy/Kotlin

# CLI

Gradle has command line tool

# Manually create simple project

- Project config file for gradle is called `build.gradle` (in Ant project is configured in `build.xml`, in Maven in `pom.xml`)
- In the project folder run `gradle init` (choose basic)
- `build.gradle` will be empty
- `gradle tasks --all` will list all default tasks - there are multiple helpful tasksm, like:
    ```
    Build Setup tasks
    -----------------
    init - Initializes a new Gradle build.
    updateDaemonJvm - Generates or updates the Gradle Daemon JVM criteria.
    wrapper - Generates Gradle wrapper files.

    Help tasks
    ----------
    buildEnvironment - Displays all buildscript dependencies declared in root project 'project-1'.
    dependencies - Displays all dependencies declared in root project 'project-1'.
    dependencyInsight - Displays the insight into a specific dependency in root project 'project-1'.
    help - Displays a help message.
    javaToolchains - Displays the detected java toolchains.
    outgoingVariants - Displays the outgoing variants of root project 'project-1'.
    projects - Displays the sub-projects of root project 'project-1'.
    properties - Displays the properties of root project 'project-1'.
    resolvableConfigurations - Displays the configurations that can be resolved in root project 'project-1'.
    tasks - Displays the tasks runnable from root project 'project-1'.

    Other tasks
    -----------
    components - Displays the components produced by root project 'project-1'. [deprecated]
    dependentComponents - Displays the dependent components of components in root project 'project-1'. [deprecated]
    model - Displays the configuration model of root project 'project-1'. [deprecated]
    prepareKotlinBuildScriptModel

    ```
- to add a new task, edit `build.gradle`:
    ```Groovy
    // Groovy    
    task firstTask {
        println 'Grale rocks!'
    }
    ```
- `gradle tasks --all` should now display the task
- to execute task run `gradle firstTask`
- another option `gradle fT` - abbreviation from the camel-case task name
- `settings.gradle` will have the project name:
    `rootProject.name = 'project-1'`

# Gradle wrapper
- Need to learn more, but Gradle wrapper is a OS shell script, which installs gradle for the project regardless if there is a global version of Gradle installed in the computer    
- Use `./gradlew` instead of `gradle`
- After the first `./gradlew` the wrapper script will download Gradle and save it into `.gradle` folder of the project (this needs to be Git-ignored!). Maven wrapper works in the same way.

# Java project

- Execute `gradle init` and choose `Application` (with Java etc)
- It creates a folder `/app` and puts `build.gradle` there. Why not in the project root? Because in some newer version of Gradle they introduced this concept of a single sub-project
- Inside `settings.gradle` there is `include('app')`, which 'imports' that project from the `app folder`
- So it is possible to store all related Gradle things in justy the project root


