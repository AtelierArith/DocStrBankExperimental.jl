```
conventionalize(flat::AbstractFourierLattice, cntr::Char) --> ::typeof(flat′)
```

与えられた `flat` は中心 `cntr` を持つ原始基底を指し、関連する従来の基底に言及する導出された（しかし物理的に同等の）格子 `flat′` を計算します。

追加の詳細については、補完メソッド [`primitivize(::AbstractFourierLattice, ::Char)`](@ref) を参照してください。
