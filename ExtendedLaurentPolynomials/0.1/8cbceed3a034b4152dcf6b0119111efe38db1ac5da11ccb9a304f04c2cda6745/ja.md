```
InvZ(p::Polynomial)
```

整数指数のみを持つ多項式 `p` に対して逆z変換を実行します。

# 例

```julia
julia> p = Polynomial([1, 2, 3, 4, 5], [-2, -1, 0, 1, 2])
z^-2 + 2*z^-1 + 3 + 4*z + 5*z^2 

julia> InvZ(p)
5-element Vector{Int64}:
 1
 2
 3
 4
 5
```
