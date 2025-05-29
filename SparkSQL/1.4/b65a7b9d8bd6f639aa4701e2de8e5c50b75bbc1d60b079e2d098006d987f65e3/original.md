# Purpose

Initializes the Java Virtual Machine (JVM) in Julia using the JavaCall package.

# Arguments

  * `JVMOptions::String`: configuration options to pass to the JVM.

# Examples

```
initJVM("-XX:ParallelGCThreads=2")
```
