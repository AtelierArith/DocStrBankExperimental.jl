s段の分割ガウス・レジェンドル・ルンゲ・クッタ・タブロー

```julia
PartitionedTableauGauss(::Type{T}, s)
PartitionedTableauGauss(s) = PartitionedTableauGauss(Float64, s)
```

コンストラクタは、段数`s`とオプションでタブローの要素型`T`を受け取ります。

この [`PartitionedTableau`](@ref) は、係数`a`と`ā`の両方に [`TableauGauss`](@ref) を使用します。
