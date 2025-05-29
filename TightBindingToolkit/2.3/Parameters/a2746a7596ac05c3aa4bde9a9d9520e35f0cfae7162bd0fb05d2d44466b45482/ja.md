`Param{T}` は、複数のボンドにまたがる一般的なタイトバインディングパラメータを表すデータ型です。

# 属性

  * `value        ::  Vector{ Float64 }`: パラメータの強度（または変更された場合の完全な履歴）。
  * `unitBonds    ::  Vector{ Bond{T} }`: このパラメータが存在するすべてのボンド。これらのボンドは「単位」強度を持つとされ、最終的には `UnitCell` を作成する際に `value` によってスケーリングされます。
  * `label        ::  String`: パラメータをマークするための文字列ラベル。
  * `dist         ::  Float64`: パラメータが存在するボンドの距離。

この構造体は次のように初期化します。

```julia
Param( value::Float64 )
Param( value::Float64 , rank::Int64 )
```
