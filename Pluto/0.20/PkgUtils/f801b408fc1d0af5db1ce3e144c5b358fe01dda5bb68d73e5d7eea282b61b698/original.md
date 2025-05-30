```julia
activate_notebook_environment(notebook_path::String; show_help::Bool=true)::Nothing
```

Activate the package environment embedded in a notebook file, for interactive use. This will allow you to use the Pkg REPL and Pkg commands to modify the environment, and any changes you make will be automatically saved in the notebook file.

More help will be displayed if `show_help` is `true`.

Limitations:

  * Shut down the notebook before using this functionality.
  * Non-interactive use is limited, use the functional form instead, or insert `sleep` calls after modifying the environment.

!!! info
    This functionality works using file watching. A dummy repository contains a copy of the embedded tomls and gets activated, and the notebook file is updated when the dummy repository changes.

