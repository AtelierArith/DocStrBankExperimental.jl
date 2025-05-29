```
const ElementInfo{T}=Union{Vector{T},VectorOfConstants{T}}
```

要素情報配列のためのUnion型です。すべての要素が同じ情報を持っている場合、それは[`VectorOfConstants`](@ref)として経済的な形式で保存できます。
