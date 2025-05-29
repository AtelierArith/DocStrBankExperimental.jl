```
customop(;with_mpi::Bool = false)
```

Create a new custom operator. Typically users call `customop` twice: the first call generates a `customop.txt`,  users edit the content in the file; the second all generates C++ source code, CMakeLists.txt, and gradtest.jl from `customop.txt`.

# Example

```julia-repl
julia> customop() # create an editable `customop.txt` file
[ Info: Edit custom_op.txt for custom operators
julia> customop() # after editing `customop.txt`, call it again to generate interface files.
```

# Options

  * `with_mpi`: Whether the custom operator uses MPI
