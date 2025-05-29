```
GenomicInterval{T} <: AbstractGenomicInterval{T}
```

ゲノム区間は、いくつかの関連メタデータを持つ区間を指定します。最初の3つのフィールド（`groupname`、`first`、および `last`）は、[`Interval`](@ref Interval) オブジェクトを構築する際の必須引数です。

# フィールド

  * `groupname::String`: 区間に関連付けられたグループ名。
  * `first::Int64`: 最も左の位置。
  * `last::Int64`: 最も右の位置。
  * `strand::Strand`: [`strand`](@ref Strand)。
  * `metadata::T`
