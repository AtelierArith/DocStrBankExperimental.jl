ソートされた `UnitRange` のセット。昇順にソートされ、どの範囲も他の範囲と重複しません。

```julia
mutable struct VecUnitRangesSortedSet{K,TU} <: AbstractSet{TU}
    "最後に使用された範囲のインデックス。"
    lastusedrangeindex::Int
    "範囲の開始位置のストレージ、"
    rstarts::Vector{K}
    "および終了位置。"
    rstops::Vector{K}
end
```

範囲は `Vector` に格納されます：`rstarts` には範囲の `first` が格納され、`rstops` には範囲の `last` が格納されます。

詳細については `UnitRangesSortedSet` を参照してください。
