```
(p::Polynomial)(x::Number)
(→)(x::Number, p::Polynomial)
```

`p` を `x` で評価します。

# 例

```julia
julia> p = Polynomial([1, 2, 3, 4, 5], [-2, -1, 0, 1, 2])
z^-2 + 2*z^-1 + 3 + 4*z + 5*z^2 

julia> p(2.3)
39.7086011342155

julia> 2.3 → p
39.7086011342155
```
