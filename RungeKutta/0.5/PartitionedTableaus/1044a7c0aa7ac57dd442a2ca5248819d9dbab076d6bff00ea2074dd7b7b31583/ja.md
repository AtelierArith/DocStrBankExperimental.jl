Gauss-Lobatto IIID-IIID̄法のためのタブロー（sステージ）

```julia
TableauLobattoIIIDIIID̄(::Type{T}, s)
TableauLobattoIIIDIIID̄(s) = TableauLobattoIIIDIIID̄(Float64, s)
```

コンストラクタは、ステージの数`s`とオプションでタブローの要素型`T`を受け取ります。

この [`PartitionedTableau`](@ref) は、`a` に対して [`TableauLobattoIIID`](@ref) を、`ā` に対して [`TableauLobattoIIID̄`](@ref) を使用します。
