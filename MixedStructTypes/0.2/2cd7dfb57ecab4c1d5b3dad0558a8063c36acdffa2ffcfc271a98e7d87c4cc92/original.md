```
@dispatch(function_definition)
```

This macro allows to dispatch on types created by [`@compact_structs`](@ref) or [`@sum_structs`](@ref). Notice that this only works when the kinds in the macro are not wrapped by any type containing them.

## Example

```julia
julia> @compact_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> @dispatch f(::A) = 1;

julia> @dispatch f(::B) = 2;

julia> @dispatch f(::Vector{B}) = 3; # this doesn't work
ERROR: UndefVarError: `B` not defined
Stacktrace:
 [1] top-level scope
   @ REPL[7]:1

julia> f(A(0))
1

julia> f(B(0))
2
```
