```
squared_hinge_loss(ŷ, y)
```

予測 `ŷ` と真のラベル `y`（1 または -1 を含む）に基づいて二乗ヒンジ損失を返します。計算式は次の通りです。

```
sum((max.(0, 1 .- ŷ .* y)).^2) / size(y, 2)
```

通常、サポートベクターマシンのような分類器と共に使用されます。詳細は [`hinge_loss`](@ref) を参照してください。

# 例

```jldoctes
julia> y_true = [1, -1, 1, 1];

julia> y_pred = [0.1, 0.3, 1, 1.5];

julia> Flux.squared_hinge_loss(y_pred, y_true)
0.625

julia> Flux.squared_hinge_loss(y_pred[1], y_true[1]) != 0
true

julia> Flux.squared_hinge_loss(y_pred[end], y_true[end]) == 0
true

julia> Flux.squared_hinge_loss(y_pred[2], y_true[2]) != 0
true
```
