```
ValOutDiGraph{V <: Integer, V_VALS, E_VALS, G_VALS, V_VALS_C, E_VALS_C} <: AbstractValGraph
```

頂点、辺、グラフの値を持つ有向単純グラフを表す型です。

# パラメータ

  * `V`: 頂点インデックスの型。`Integer`の具体的なサブタイプである必要があります。
  * `V_VALS`: 頂点の値の型、`Tuple`または`NamedTuple`のいずれか。
  * `E_VALS`: 辺の値の型、`Tuple`または`NamedTuple`のいずれか。
  * `G_VALS`: 辺の値の型、`Tuple`または`NamedTuple`のいずれか。
  * `V_VALS_C`: 内部ストレージパラメータで、`V_VALS`から導出されます。
  * `E_VALS_C`: 内部ストレージパラメータで、`E_VALS`から導出されます。

内部パラメータ`V_VALS_C`と`E_VALS_C`は、コンストラクタによって自動的に計算されるため、通常は手動で指定する必要はありません。

`ValDiGraph`よりもメモリを少なく使用し、出力エッジのみを保存します。
