```
ValDiGraph{V <: Integer, V_VALS, E_VALS, G_VALS, V_VALS_C, E_VALS_C} <: AbstractValGraph
```

頂点、エッジ、グラフの値を持つ有向単純グラフを表す型です。

# パラメータ

  * `V`: 頂点インデックスの型。`Integer`の具体的なサブタイプである必要があります。
  * `V_VALS`: 頂点の値の型、`Tuple`または`NamedTuple`のいずれか。
  * `E_VALS`: エッジの値の型、`Tuple`または`NamedTuple`のいずれか。
  * `G_VALS`: エッジの値の型、`Tuple`または`NamedTuple`のいずれか。
  * `V_VALS_C`: 内部ストレージパラメータで、`V_VALS`から派生します。
  * `E_VALS_C`: 内部ストレージパラメータで、`E_VALS`から派生します。

内部パラメータ`V_VALS_C`と`E_VALS_C`は、コンストラクタによって自動的に計算されるため、通常は手動で指定する必要はありません。

`ValOutDiGraph`よりも多くのメモリを使用し、出力エッジだけでなく、逆エッジも保存します。
