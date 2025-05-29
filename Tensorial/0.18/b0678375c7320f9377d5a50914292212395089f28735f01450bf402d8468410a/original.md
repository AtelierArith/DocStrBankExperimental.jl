```
contract(x, y, ::Val{N})
```

Conduct contraction of `N` inner indices. For example, `N=2` contraction for third-order tensors $A_{ij} = B_{ikl} C_{klj}$ can be computed as follows:

# Examples

```jldoctest
julia> B = rand(Tensor{Tuple{3,3,3}});

julia> C = rand(Tensor{Tuple{3,3,3}});

julia> A = contract(B, C, Val(2))
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 3.70978  2.47156  3.91807
 2.90966  2.30881  3.25965
 1.78391  1.38714  2.2079
```

The following infix operators are also available for specific contractions:

  * `x ⊡ y` (where `⊡` can be typed by `\boxdot<tab>` ): `contract(x, y, Val(1))`
  * `x ⊡₂ y` (where `⊡₂` can be typed by `\boxdot<tab>\_2<tab>` ): `contract(x, y, Val(2))`
  * `x ⊗ y` (where `⊗` can be typed by `\otimes<tab>` ): `contract(x, y, Val(0))`
