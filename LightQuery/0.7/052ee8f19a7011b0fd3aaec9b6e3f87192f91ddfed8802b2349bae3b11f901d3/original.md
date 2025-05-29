```
order(unordered, key_function; keywords...)
```

Generalized sort. `keywords` will be passed to `sort!`; see the documentation there for options. Use [`By`](@ref) to mark that an object has been sorted. If the results of `key_function` are type unstable, consider using `hash ∘ key_function` instead.

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> collect(@inferred order([-2, 1], abs))
2-element Array{Int64,1}:
  1
 -2
```
