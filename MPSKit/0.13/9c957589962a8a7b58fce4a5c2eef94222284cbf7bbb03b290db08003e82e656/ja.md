```
WindowArray{T} <: AbstractVector{T}
```

左右に周期的な環境に埋め込まれたベクトルで、任意の整数インデックスでアクセスできます。`middle`部分は通常の`Vector{T}`であり、`left`および`right`部分は`PeriodicVector{T}`です。

このベクトルは、長さや軸を含む中間部分からほとんどのプロパティを継承します。それにもかかわらず、インデックス操作はオーバーロードされており、範囲外アクセスを許可し、周期的な環境によって解決されます。

詳細は[`PeriodicVector`](@ref)を参照してください。
