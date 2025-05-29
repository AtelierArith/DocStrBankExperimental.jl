```
setup_workspace(build_path::String, sources::Vector{SetupSource};
                verbose::Bool = false)
```

Sets up a workspace within `build_path`, creating the directory structure needed by further steps, unpacking the source within `build_path`, and defining the environment variables that will be defined within the sandbox environment.

This method returns the `Prefix` to install things into, and the runner that can be used to launch commands within this workspace.
