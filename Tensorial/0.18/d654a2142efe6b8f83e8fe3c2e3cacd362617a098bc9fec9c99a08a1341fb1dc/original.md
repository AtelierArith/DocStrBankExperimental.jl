```
tensor(x::AbstractTensor, y::AbstractTensor)
x ⊗ y
```

Compute tensor product such as $A_{ij} = x_i y_j$. `x ⊗ y` (where `⊗` can be typed by `\otimes<tab>`) is a synonym for `tensor(x, y)`.

# Examples

```jldoctest
julia> x = rand(Vec{3})
3-element Vec{3, Float64}:
 0.32597672886359486
 0.5490511363155669
 0.21858665481883066

julia> y = rand(Vec{3})
3-element Vec{3, Float64}:
 0.8942454282009883
 0.35311164439921205
 0.39425536741585077

julia> A = x ⊗ y
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.291503  0.115106   0.128518
 0.490986  0.193876   0.216466
 0.19547   0.0771855  0.086179
```
