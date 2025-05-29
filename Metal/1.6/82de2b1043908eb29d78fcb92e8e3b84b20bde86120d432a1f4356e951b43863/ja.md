```
mtl(A; storage=Metal.PrivateStorage)
```

`storage` は `Metal.PrivateStorage`（デフォルト）、`Metal.SharedStorage`、または `Metal.ManagedStorage` であることができます。

意見を持ったGPU配列アダプタであり、配列の要素型 `T` を変更する可能性があります：

  * `T<:AbstractFloat` の場合、パフォーマンスと互換性の理由から `MtlArray{Float32}` を作成します（`Float16` を除く）。
  * `T<:Complex{<:AbstractFloat}` の場合、`MtlArray{ComplexF32}` を作成します。
  * その他の `isbitstype(T)` の場合、`MtlArray{T}` を作成します。

対照的に、`MtlArray(A)` は要素型を決して変更しません。

いくつかのラッパー構造体の内部で動作するために Adapt.jl を使用します。

# 例

```jldoctests
julia> mtl(ones(3)')
1×3 adjoint(::MtlVector{Float32, Metal.PrivateStorage}) with eltype Float32:
 1.0  1.0  1.0

julia> mtl(zeros(1,3); storage=Metal.SharedStorage)
1×3 MtlMatrix{Float32, Metal.SharedStorage}:
 0.0  0.0  0.0

julia> mtl(1:3)
1:3

julia> MtlArray(1:3)
3-element MtlVector{Int64, Metal.PrivateStorage}:
 1
 2
 3
```
