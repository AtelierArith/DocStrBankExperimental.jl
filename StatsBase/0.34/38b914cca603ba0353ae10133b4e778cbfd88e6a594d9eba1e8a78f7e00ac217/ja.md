```
addcounts!(r, x, levels::UnitRange{<:Integer}, [wv::AbstractWeights])
```

`levels`の各値の`x`における出現回数を既存の配列`r`に追加します。各`xi ∈ x`について、`xi == levels[j]`であれば、`r[j]`をインクリメントします。

重みベクトル`wv`が指定されている場合、重みの合計が生のカウントの代わりに使用されます。
