```
butcher_representation(t::RootedTree)
```

Returns the representation of `t::RootedTree` introduced by Butcher as a string. Thus, the rooted tree consisting whose only vertex is the root itself is represented as `τ`. The representation of other trees is defined recursively; if `t₁, t₂, ... tₙ` are the [`subtrees`](@ref) of the rooted tree `t`, it is represented as `t = [t₁ t₂ ... tₙ]`. If multiple subtrees are the same, their number of occurrences is written as a power.

# Examples

```jldoctest
julia> rootedtree([1, 2, 3, 2]) |> butcher_representation
"[[τ]τ]"

julia> rootedtree([1, 2, 3, 3, 2]) |> butcher_representation
"[[τ²]τ]"
```

# References

Section 300 of

  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2008.
