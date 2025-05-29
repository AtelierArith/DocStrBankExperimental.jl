```
LaurentUp(p::Polynomial)
```

pをアップスケールします。

# 例

```julia
julia> p = Polynomial([1, 2, 3, 4, 5], [-2, -1, 0, 1, 2])
z^-2 + 2*z^-1 + 3 + 4*z + 5*z^2 

julia> LaurentUp(p)
z^-4 + 2*z^-2 + 3 + 4*z^2 + 5*z^4
```
