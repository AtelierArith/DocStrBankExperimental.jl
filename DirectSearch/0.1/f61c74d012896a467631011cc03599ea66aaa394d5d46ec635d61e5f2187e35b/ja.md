```
AddProgressiveCollection(p::Constraints{FT}; h_max=Inf, h_max_update::Function=h_max_update,
                         aggregator::Function=x->max(0,x)^2)::CollectionIndex where {FT<:AbstractFloat}
```

問題内に新しい制約コレクションをインスタンス化します。この新しいコレクションを参照するインデックスを返します。

デフォルトの制約設定は、Audet & Dennis 2009のものと一致します：

`h_max`: 無限大から始まります

`h_max_update`: イテレーションが改善されている場合、h_maxを最大の有効なh評価に設定します

`aggregator`: $k=\max(0,x)^2$ の場合に $h$ を $\sum k(x)$ として作成します
