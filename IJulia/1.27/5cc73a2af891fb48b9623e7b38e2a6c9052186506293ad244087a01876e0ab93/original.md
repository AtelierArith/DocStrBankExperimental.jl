```
notebook(; dir=homedir(), detached=false, port::Union{Nothing,Int}=nothing)
```

The `notebook()` function launches the Jupyter notebook, and is equivalent to running `jupyter notebook` at the operating-system command-line.    The advantage of launching the notebook from Julia is that, depending on how Jupyter was installed, the user may not know where to find the `jupyter` executable.

By default, the notebook server is launched in the user's home directory, but this location can be changed by passing the desired path in the `dir` keyword argument.  e.g. `notebook(dir=pwd())` to use the current directory.

By default, `notebook()` does not return; you must hit ctrl-c or quit Julia to interrupt it, which halts Jupyter.  So, you must leave the Julia terminal open for as long as you want to run Jupyter.  Alternatively, if you run `notebook(detached=true)`, the `jupyter notebook` will launch in the background, and will continue running even after you quit Julia.  (The only way to stop Jupyter will then be to kill it in your operating system's process manager.)

When the optional keyword `port` is not `nothing`, open the notebook on the given port number.

For launching a JupyterLab instance, see [`IJulia.jupyterlab()`](@ref).
