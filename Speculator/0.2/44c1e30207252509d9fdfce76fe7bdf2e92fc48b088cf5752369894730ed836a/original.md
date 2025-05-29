```
install_speculator(
    predicate = (m, _) -> m ∉ [Base, Core];
background::Bool = true, parameters...)
```

Install a hook that calls `speculate(predicate, value; background, parameters...)` on each input `value` in the REPL.

Subsequent calls to this function may be used to replace the hook. The hook may be removed using [`uninstall_speculator`](@ref). This function has no effect in non-interactive sessions.

See also [`speculate`](@ref).

!!! tip
    Use this in a `startup.jl` file to reduce latency in the REPL. Since it relies on the REPL being initialized, it should be placed at the end of the file.


```julia-repl
julia> install_speculator(; limit = 2, verbosity = debug)

julia> f() = nothing;

[ Info: Compiled `Main.f()`
julia> g(::Union{String, Symbol}) = nothing;

[ Info: Compiled `Main.g(::Symbol)`
[ Info: Compiled `Main.g(::String)`
```
