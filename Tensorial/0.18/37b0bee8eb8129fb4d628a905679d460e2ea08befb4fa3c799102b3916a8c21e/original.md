```
levicivita(::Val{N} = Val(3))
```

Return `N` dimensional Levi-Civita tensor.

# Examples

```jldoctest
julia> ϵ = levicivita()
3×3×3 Tensor{Tuple{3, 3, 3}, Int64, 3, 27}:
[:, :, 1] =
 0   0  0
 0   0  1
 0  -1  0

[:, :, 2] =
 0  0  -1
 0  0   0
 1  0   0

[:, :, 3] =
  0  1  0
 -1  0  0
  0  0  0
```
