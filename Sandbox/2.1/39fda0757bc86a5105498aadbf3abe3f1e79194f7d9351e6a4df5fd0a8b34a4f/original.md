```
SandboxConfig(read_only_maps, read_write_maps, env)
```

Sandbox executors require a configuration to set up the environment properly.

  * `read_only_maps`: Directories that are mapped into the sandbox as read-only mappings.

      * Specified as pairs, e.g. `sandbox_path => host_path`.  All paths must be absolute.
      * Must always include a mapping for root, e.g. `"/" => rootfs_path`.
  * `read_write_maps`: Directories that are mapped into the sandbox as read-write mappings.

      * Specified as pairs, e.g. `sandbox_path => host_path`.  All paths must be absolute.
      * Note that some executors may not show perfect live updates; consistency is guaranteed only after execution is finished.
  * `env`: Dictionary mapping of environment variables that should be set within the sandbox.
  * `entrypoint`: Executable that gets passed the actual command being run.

      * This is a path within the sandbox, and must be absolute.
      * Defaults to `nothing`, which causes the command to be executed directly.
  * `pwd`: Set the working directory of the command that will be run.

      * This is a path within the sandbox, and must be absolute.
  * `persist`: Tell the executor object to persist changes made to the rootfs.

      * This is a boolean value, it is up to interpretation by the executor.
      * Persistence is a property of an individual executor and changes live only as long as the executor object itself.
      * You cannot transfer persistent changes from one executor to another.
  * `multiarch`: Request multiarch executable support

      * This is an array of `Platform` objects
      * Sandbox will ensure that interpreters (such as `qemu-*-static` binaries) are available for each platform.
      * Requesting multiarch support for a platform that we don't support results in an `ArgumentError`.
  * `uid` and `gid`: Numeric user and group identifiers to spawn the sandboxed process as.

      * By default, these are both `0`, signifying `root` inside the sandbox.
  * `stdin`, `stdout`, `stderr`: input/output streams for the sandboxed process.

      * Can be any kind of `IO`, `TTY`, `devnull`, etc...
  * `hostname`: Set the hostname within the sandbox, defaults to the current hostname
  * `verbose`: Set whether the sandbox construction process should be more or less verbose.
