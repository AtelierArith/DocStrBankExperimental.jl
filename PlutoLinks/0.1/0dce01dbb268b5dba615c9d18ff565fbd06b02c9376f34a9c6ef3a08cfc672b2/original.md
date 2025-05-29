Watch a Julia source file and loads its content as a module. The loaded module is then reloaded automatically whenever the file changes.

```julia
MyModule = @ingredients("my_exported_function.jl")
```
