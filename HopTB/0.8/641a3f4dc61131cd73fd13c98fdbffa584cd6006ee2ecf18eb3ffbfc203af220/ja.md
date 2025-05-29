```julia
addhopping!(tm::TBModel, R::AbstractVector{<:Integer}, hopping::Matrix{<:Number})
```

`tm`のハミルトニアンに`hopping`を追加します。

`hopping`は、nおよびmインデックスを持つ行列⟨0n|H|Rm⟩を含む`(tm.norbits, tm.norbits)`配列である必要があります。もしRが[0, 0, 0]であれば、`hopping`はエルミートである必要があります。
