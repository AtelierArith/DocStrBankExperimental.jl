```
精度
```

Precision-at-$k$ (Precision@$k$) は、真の正例の割合に基づいて、トップ-$k$（`topk`）推薦リスト $I_N(u)$ の正確性を評価します：

$$
\mathrm{Precision@}k = \frac{|\mathcal{I}^+_u \cap I_N(u)|}{|I_N(u)|}.
$$

```
measure(
    metric::Precision,
    truth::AbstractVector{T},
    pred::AbstractVector{T},
    topk::Integer
)
```
