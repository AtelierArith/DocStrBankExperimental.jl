```
is_zero_cycle(n, d, m, P)
```

Return `true` if the equivariant class `P` is a 0-cycle in the moduli space, `false` otherwise.

# Arguments

  * `n::Int64`: the dimension of the projective space.
  * `deg::Int64`: the degree of the stable maps.
  * `n_marks::Int64`: the number of marks.
  * `P`: the equivariant class.

# Example

```julia-repl
julia> P = Hypersurface(g,c,w,s,5);
julia> is_zero_cycle(4,1,0,P)
true
```
