```
@pattern(function_definition)
```

This macro allows to pattern on types created by [`@sum_structs`](@ref). 

Notice that this only works when the kinds in the macro are not wrapped  by any type containing them.

## Example

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> @pattern f(::AB'.A) = 1;

julia> @pattern f(::AB'.B) = 2;

julia> @pattern f(::Vector{AB}) = 3; # this works 

julia> @pattern f(::Vector{AB'.B}) = 3; # this doesn't work
ERROR: LoadError: It is not possible to dispatch on a variant wrapped in another type
...

julia> f(AB'.A(0))
1

julia> f(AB'.B(0))
2

julia> f([AB'.A(0), AB'.B(0)])
3
```
