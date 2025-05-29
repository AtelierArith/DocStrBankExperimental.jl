```
struct ProductSpace{S<:ElementarySpace, N} <: CompositeSpace{S}
```

`ProductSpace`は、タイプ`S<:ElementarySpace`の`N`個のベクトル空間のテンソル積空間です。同じタイプの[`ElementarySpace`](@ref)オブジェクト間のテンソル積のみが許可されています。
