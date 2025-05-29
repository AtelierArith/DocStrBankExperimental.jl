```
hinge_loss(ŷ, y; agg = mean)
```

予測 `ŷ` と真のラベル `y`（1 または -1 を含む）に基づいて、[hinge_loss](https://en.wikipedia.org/wiki/Hinge_loss) を返します。計算式は次の通りです。

```
sum(max.(0, 1 .- ŷ .* y)) / size(y, 2)
```

通常、サポートベクターマシンのような分類器と共に使用されます。詳細は [`squared_hinge_loss`](@ref) を参照してください。

# 例

```jldoctest
julia> y_true = [1, -1, 1, 1];

julia> y_pred = [0.1, 0.3, 1, 1.5];

julia> Flux.hinge_loss(y_pred, y_true)
0.55

julia> Flux.hinge_loss(y_pred[1], y_true[1]) != 0  # 同じ符号だが |ŷ| < 1
true

julia> Flux.hinge_loss(y_pred[end], y_true[end]) == 0  # 同じ符号だが |ŷ| >= 1
true

julia> Flux.hinge_loss(y_pred[2], y_true[2]) != 0 # 符号が逆
true
```
