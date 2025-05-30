```
NDCG
```

MPRと同様に、正規化割引累積ゲイン（NDCG）は、より高いランクの真のポジティブに重点を置いた$I(u)$のスコアを計算します。NDCGとMPRの違いは、NDCGが$\mathcal{I}^+_u$内で期待されるランキングを指定できる点です。つまり、このメトリックは、$n$-番目のサンプルが推薦リストのトップにランク付けされる可能性を示唆する関連スコア$\mathrm{rel}_n$を組み込むことができ、真のサンプルの期待されるランキングに直接対応します。

```
measure(
    metric::NDCG,
    truth::AbstractVector{T},
    pred::AbstractVector{T},
    topk::Integer
)
```
