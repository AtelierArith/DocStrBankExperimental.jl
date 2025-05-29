```
SandboxExecutor
```

This represents the base type for all execution backends within this package. Valid concrete subtypes must implement at least the following methods:

  * `T()`: no-argument constructor to ready an execution engine with all defaults.
  * `executor_available(::DataType{T})`: Checks whether executor type `T` is available on this system.  For example, `UserNamespacesExecutor`s are only available on Linux, and even then only on certain kernels.  Availablility checks may run a program to determine whether that executor is actually available.
  * `build_executor_command(exe::T, config::SandboxConfig, cmd::Cmd)`: Builds the `Cmd` object that, when run, executes the user's desired command within the given sandbox.  The `config` object contains all necessary metadata such as shard mappings, environment variables, `stdin`/`stdout`/`stderr` redirection, etc...
  * `cleanup(exe::T)`: Cleans up any persistent data storage that this executor may have built up over the course of its execution.

Note that while you can manually construct and cleanup an executor, it is recommended that users instead make use of the `with_executor()` convenience function:

```
with_executor(UnprivilegedUserNamespacesExecutor) do exe
    run(exe, config, ...)
end
```
