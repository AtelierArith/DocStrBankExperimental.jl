```
get_output(::Client, ::Union{MBQC,ComputationRound}, mg)
```

クライアントのメタグラフから計算の出力を取得します。この関数はメタグラフから出力インデックスを取得し、それらを反復処理して各インデックスの結果を取得し、結果をリストに格納します。結果のリストが返されます。

# 引数

  * `::Client`: `Client` インスタンス。
  * `::Union{MBQC,ComputationRound}`: `MBQC` または `ComputationRound` のインスタンス。
  * `mg`: クライアントのメタグラフ。

# 戻り値

  * `Array`: 結果の配列。

# 例

```julia
mg = create_meta_graph(Client())
outcomes = get_output(Client(), ComputationRound(), mg)
```
