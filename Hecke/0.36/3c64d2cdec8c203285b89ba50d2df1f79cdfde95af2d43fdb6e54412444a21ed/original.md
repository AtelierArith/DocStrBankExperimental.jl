```
 generic_group(G, op)
```

Compute a group on the set $G$ with operation $op$.

Returns a triple `(Gen, GtoGen, GentoG)`, where `Gen` is a group, `GtoGen` is a dictionary mapping elements in `G` to elements of `Gen`, and `GentoG` is likewise but the other way around.

# Examples

```jldoctest
julia> G = [1, -1, im, -im]
4-element Vector{Complex{Int64}}:
  1 + 0im
 -1 + 0im
  0 + 1im
  0 - 1im

julia> Gen, GtoGen, GentoG = generic_group(G, *);

julia> Gen
Generic group of order 4 with multiplication table

julia> one(Gen)
(1)

julia> GentoG[one(Gen)]
1 + 0im

julia> GtoGen[-1]
(2)
```
