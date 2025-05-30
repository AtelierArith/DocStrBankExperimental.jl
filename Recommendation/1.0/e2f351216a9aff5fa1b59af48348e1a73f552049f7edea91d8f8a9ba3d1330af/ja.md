```
リコール
```

Recall-at-$k$ (Recall@$k$) は、トップ-$k$ (`topk`) 推薦の結果としての真実サンプルのカバレッジを示します。この値は次の式によって計算されます：

$$
\mathrm{Recall@}k = \frac{|\mathcal{I}^+_u \cap I_N(u)|}{|\mathcal{I}^+_u|}.
$$

ここで、$|\mathcal{I}^+_u \cap I_N(u)|$ は *真陽性* の数です。

```
measure(
    metric::Recall,
    truth::AbstractVector{T},
    pred::AbstractVector{T},
    topk::Integer
)
```
