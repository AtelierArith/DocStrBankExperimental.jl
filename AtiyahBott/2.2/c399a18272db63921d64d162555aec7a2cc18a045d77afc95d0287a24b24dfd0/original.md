```
codim(n, d, m, P)
```

The codimension of the equivariant class `P`.

# Arguments

  * `n::Int64`: the dimension of the projective space.
  * `d::Int64`: the degree of the stable maps.
  * `m::Int64`: the number of marks.
  * `P`: the equivariant class.

# Example

```julia-repl
julia> P = Hypersurface(g,c,w,s,5);
julia> codim(4,1,0,P)
6
```
