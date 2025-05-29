```
generate_stubs(conn::KRPCConnection; save_file::Bool=false)
```

Generate (and `eval`) the stubs offered by the server at `conn`. If `save_file` is `true`, then the stubs will be saved into the package's directory and will be imported the next time the wrapper is loaded.

Note that world-age restricts the use of the generated and eval'ed stubs until after the latest age can be accessed, either by returning to the REPL, using Base.invokelatest, or through another call to `eval`. Keep this in mind if writing a monolithic script - a function that calls generate_stubs won't be able to immediately access the new definitions.

For more information on world age, see the documentation at https://docs.julialang.org/en/v1/manual/methods/#Redefining-Methods-1 or the paper on the topic at https://arxiv.org/abs/2010.07516.

# Examples

```julia-repl
julia> generate_stubs(conn)
```
