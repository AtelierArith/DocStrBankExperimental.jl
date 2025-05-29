```
updatestate!(model::SimModel, u, d=[]) -> xnext
```

現在の入力 `u` と測定分布 `d` を使用して `model.x0` の状態を次の時間ステップのために更新します。

このメソッドは、次の時間ステップのモデル状態 $\mathbf{x}(k+1)$ を計算して返します。

# 例

```jldoctest
julia> model = LinModel(ss(1.0, 1.0, 1.0, 0, 1.0));

julia> x = updatestate!(model, [1])
1-element Vector{Float64}:
 1.0
```
