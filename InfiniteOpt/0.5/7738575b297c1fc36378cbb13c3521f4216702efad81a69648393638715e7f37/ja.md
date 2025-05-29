```
ParameterFunction{F <: Function, VT <: VectorTuple}
```

無限のパラメータの既知の関数を格納するための `DataType` です。これらは、無限のパラメータ `parameter_refs` のサポートインスタンスを入力として受け取り、`func` を介してスカラー値を出力として計算する任意の関数に相当します。これらは [`ParameterFunctionRef`](@ref)s を介して式に組み込むことができます。

**フィールド**

  * `func::F`: 無限のパラメータを入力として受け取り、スカラー数値を出力として提供する関数。
  * `parameter_refs::VT`: `func` への入力として機能する無限のパラメータ参照。これらのフォーマットは無限の変数のそれに類似しています。
  * `parameter_nums::Vector{Int}`: `parameter_refs` のパラメータ番号。
  * `object_nums::Vector{Int}`: `parameter_refs` に関連付けられたパラメータオブジェクト番号。
