```
MaskedRegularization
```

ネストされた正則化項で、マスクが `true` の `x` の要素にのみ `prox!` と `norm` を適用します。

# 例

```julia
julia> positive = PositiveRegularization();

julia> masked = MaskedRegularization(reg, [true, false, true, false]);

julia> prox!(masked, fill(-1, 4))
4-element Vector{Float64}:
  0.0
 -1.0
  0.0
 -1.0
```
