```
intersect!(result::Vector{UnitRange{T}}, target::AbstractUnitRange, rn::RangeNode{T}) where {T}
```

`target`を`rn`に根ざす木の区間と再帰的に交差させます。

非空の交差は、交差するノードが木に現れる順序で`result`にプッシュされます。`maxlast`を保存することで、ノードの`maxlast`が`first(target)`より小さい場合に先行深さ優先探索を切り捨てることができます。ノードは`first(intvl)`の非減少順にあるため、`last(target) < first(intvl)`のときは右部分木をスキップできます。
