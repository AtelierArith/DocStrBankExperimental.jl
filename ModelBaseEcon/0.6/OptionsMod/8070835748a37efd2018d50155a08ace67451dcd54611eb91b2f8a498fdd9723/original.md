```
Options
```

A collection of key-value pairs representing the options controlling the behaviour or the definition of a Model object. The key is the option name and is always a Symbol, or converted to Symbol, while the value can be anything.

The options can be accessed using dot notation. Functions [`getoption`](@ref) and [`setoption!`](@ref) are also provided. They can be used for programmatic processing of options as well as when the option name is not a valid Julia identifier.

See also: [`Options`](@ref), [`getoption`](@ref), [`getoption!`](@ref), [`setoption!`](@ref)

# Examples

```jldoctest
julia> o = Options(maxiter=20, tol=1e-7)
Options:
    maxiter=20
    tol=1.0e-7

julia> o.maxiter = 25
25

julia> o
Options:
    maxiter=25
    tol=1.0e-7

```
