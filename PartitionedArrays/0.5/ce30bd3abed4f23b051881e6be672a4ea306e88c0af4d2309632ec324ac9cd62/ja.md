```
partition_from_color(ranks,global_to_color;multicast=false,source=MAIN)
```

引数 `global_to_color` を定義することで任意の1次元パーティションを構築します（下記参照）。出力は、パーティションの各コンポーネントにおけるインデックスを含むベクトルのベクトルです。結果の `eltype` は [`AbstractLocalIndices`](@ref) インターフェースを実装しています。

# 引数

  * `ranks`: ランクの分布を含む配列。
  * `global_to_color`: `multicast==false` の場合、 `global_to_color[gid]` はグローバルID `gid` を所有するパートIDを含みます。`multicast==true` の場合、 `global_to_color[source][gid]` はグローバルID `gid` を所有するパートIDを含みます。

# キーワード引数

  * `multicast=false`
  * `source=MAIN`

この関数は、METISのようなグラフパーティショナーを使用してパーティションを生成する際に便利です。引数 `global_to_color` はそのようなツールの通常の出力です。
