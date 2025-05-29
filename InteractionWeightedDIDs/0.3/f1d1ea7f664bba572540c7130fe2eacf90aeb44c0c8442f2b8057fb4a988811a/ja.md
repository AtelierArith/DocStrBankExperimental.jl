```
GroupFEterms <: StatsStep
```

[`InteractionWeightedDIDs.groupfeterms`](@ref)を呼び出して、オブジェクトIDに基づく後の比較を可能にするために、等価性（`hash`）によってグループ化された`feterms`のインスタンスの1つを取得します。

このステップは、[`@specset`](@ref)および[`proceed`](@ref)を使用している場合にのみ有用です。
