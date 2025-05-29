```
HSPRHeuristic(op::Function)
```

後方探索のための緩和された計画グラフヒューリスティックのファミリーで、HSPrプランナーによって導入されました（「r」は回帰を意味します）[1]。条件を達成するためのコストは、前方バリアント[`HSPHeuristic`](@ref)と同じ方法で推定されますが、この推定はヒューリスティックの事前計算中に一度だけ行われます。ヒューリスティック評価中、現在の部分状態から開始状態へのコストは、部分状態で真である各条件の集約コストとして推定されます。

[1] B. Bonet and H. Geffner, "Planning as Heuristic Search," Artificial Intelligence, vol. 129, no. 1, pp. 5–33, Jun. 2001, [https://doi.org/10.1016/S0004-3702(01)00108-4](https://doi.org/10.1016/S0004-3702(01)00108-4).
