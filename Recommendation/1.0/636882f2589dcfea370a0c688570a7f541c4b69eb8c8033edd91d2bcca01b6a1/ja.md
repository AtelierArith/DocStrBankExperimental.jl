```
get_pairwise_preference_triples(R::AbstractMatrix) -> Vector{Tuple{Int, Int, Int}}
```

ユーザー-アイテム行列 `R` に対応するユーザー-アイテム-アイテムのトリプルを返します（すなわち、$(u, i, j) \in D_s$ は [BPR: Bayesian Personalized Ranking from Implicit Feedback](https://dl.acm.org/doi/10.5555/1795114.1795167) におけるものです）。ペアワイズアイテムランキングの文脈では、各トリプルはユーザー $u$ がアイテム $i$ をアイテム $j$ よりも好むことを表します。
