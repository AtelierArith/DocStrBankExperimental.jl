```
function derivation_heuristic(::TopDownIterator, indices::Vector{Int})
```

穴を埋めるために最も有望なルールに基づいて、`indices`のソートされたサブリストを返します。基盤となるソルバーは、Holeのドメイン内で順序を変更できます。列挙順序を明示的かつ予測可能にするために、ドメインをソートします。
