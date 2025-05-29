```
assemble_diagonal!(op::Operator, diag::CeedVector; request=RequestImmediate())
```

与えられた [`CeedVector`](@ref) に線形 [`Operator`](@ref) の対角成分を追加します。

!!! note "注意:"
    現在、単一フィールドを持つ [`Operator`](@ref) のみがサポートされています。

