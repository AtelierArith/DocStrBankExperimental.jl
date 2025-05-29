```
speculate(predicate, value; parameters...)
speculate(value; parameters...)
```

Search for compilable methods.

See also [`install_speculator`](@ref).

!!! tip
    Use this in a package to reduce latency.


!!! note
    This only runs when called during precompilation or an interactive session, or when writing precompilation directives to a file.


# Parameters

  * `predicate = Returns(true)`:   This must accept the signature `predicate(::Module, ::Symbol)::Bool`.   Returning `true` specifies to search `getproperty(::Module, ::Symbol)`,   whereas returning `false` specifies to skip the value.   This is called when searching the names of a `Module` if the   given module and name satisfy `isdefined` and `!isdeprecated`,   and is called when searching for types from method parameters.   The default predicate `Returns(true)` will search every value,   whereas the predicate `Returns(false)` will not search any value.   Some useful predicates include `Base.isexported`,   `Base.ispublic`, and checking properties of the value itself.
  * `value`:   When given a `Module`, `speculate` will recursively search its contents   using `names(::Module; all = true)`, for each defined value that   is not deprecated, is not an external module, and satisifes the `predicate`.   For other values, each of their generic `methods`   are searched for corresponding compilable methods.

# Keyword parameters

  * `background::Bool = false`:   Specifies whether to run on a thread in the `:default` pool.   The number of available threads can be determined using `Threads.nthreads(:default)`.
  * `dry::Bool = false`:   Specifies whether to run `precompile` on generated method signatures.   This is useful for testing with `verbosity = debug ∪ review`.   Method signatures that are known to be specialized are skipped.   Note that `dry` must be `false` to save the directives to a file with the `path` parameter.
  * `limit::Int = 1`:   Specifies the maximum number of compilable methods that are generated from a generic method.   Values less than `1` will throw an error.   Otherwise, method signatures will be generated from the Cartesian product each parameter type.   Concrete types and those marked with `@nospecialize` are used directly.   Otherwise, concrete types are obtained from the subtypes of `DataType` and `Union`.   Setting an appropriate value prevents spending too   much time precompiling a single generic method.
  * `path::String = ""`:   Saves successful precompilation directives to a file   if the `path` is not empty and it is not a `dry` run.   Generated methods that are known to have been compiled are skipped.   The resulting directives may require loading additional modules to run.
  * `verbosity::Verbosity = warn`:   Specifies what logging statements to show.   If this function is used to precompile a package,   this should be set to [`silent`](@ref) or [`warn`](@ref).   See also [`Verbosity`](@ref).

# Examples

```julia-repl
julia> module Showcase
           export g, h

           f() = nothing
           g(::Int) = nothing
           h(::Union{String, Symbol}) = nothing
       end;

julia> speculate(Showcase; verbosity = debug)
[ Info: Compiled `Main.Showcase.g(::Int)`
[ Info: Compiled `Main.Showcase.f()`

julia> speculate(Base.isexported, Showcase; verbosity = debug)
[ Info: Skipped `Main.Showcase.g(::Int)`

julia> speculate(Showcase.h; verbosity = debug) do m, n
           !(m == Core && n == :String)
       end
[ Info: Compiled `Main.Showcase.h(::Symbol)`

julia> speculate(Showcase.h; limit = 2, verbosity = debug)
[ Info: Skipped `Main.Showcase.h(::String)`
[ Info: Compiled `Main.Showcase.h(::Symbol)`
```
