```
assemble_diagonal!(op::Operator, diag::CeedVector; request=RequestImmediate())
```

線形[`Operator`](@ref)の対角成分で[`CeedVector`](@ref)を上書きします。

!!! note "注意:"
    現在、単一フィールドを持つ[`Operator`](@ref)のみがサポートされています。

