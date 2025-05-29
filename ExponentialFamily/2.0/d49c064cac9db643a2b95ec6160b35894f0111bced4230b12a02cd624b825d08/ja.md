```
isbasemeasureconstant(something)
```

`something`の自然パラメータに関してベース測度が定数であるかどうかに応じて、`NonConstantBaseMeasure()`または`ConstantBaseMeasure()`のいずれかを返します。デフォルトでは、パッケージは`Function`の形式のベース測度は定数ではないと仮定します。しかし、単に定数を返すベース測度に関してはこれは真ではありません。そのような場合、`isbasemeasureconstant`は特定のメソッドを持たなければなりません。

参照: [`getbasemeasure`](@ref), [`basemeasure`](@ref)
