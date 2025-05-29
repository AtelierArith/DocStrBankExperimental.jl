```
istrans(vi::AbstractVarInfo[, vns::Union{VarName, AbstractVector{<:Varname}}])
```

`vi`が制約のない空間で動作している場合は`true`を返し、`vi`が対応する分布のサポート内に実現があると仮定している場合は`false`を返します。

`vns`が提供されている場合、これ/これらの変数名が変換されているかどうかのみを確認します。

!!! 警告     `AbstractVarInfo`のすべての実装が、変数のサブセットのみを変換することをサポートしているわけではありません。
