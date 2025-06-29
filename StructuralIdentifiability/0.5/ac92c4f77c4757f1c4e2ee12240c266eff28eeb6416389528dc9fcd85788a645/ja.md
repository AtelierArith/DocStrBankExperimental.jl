```
linear_compartment_model(graph; inputs = [], outputs = [], leaks = [])
```

入力: ノードが1から`n`まで番号付けされた線形コンパートメントモデルを定義します。

  * `graph` - グラフの隣接リストを表す整数配列の配列
  * `inputs` - 入力ノードの配列
  * `outputs` - 出力ノードの配列
  * `leaks` - シンクノードの配列

出力:

  * 標準表記の対応するODEシステム (例えば、[この論文](https://doi.org/10.1007/s11538-015-0098-0)のように)

例: 4つのノードを持つ双方向サイクルを考えます。その隣接リストは次のように書くことができます。

```
[ [2, 4], [1, 3], [2, 4], [1, 3] ]
```

上のリストでは、`i`番目の要素は、頂点`i`からエッジが存在する頂点のリストです。これで、出力が頂点1、入力が頂点2、漏れが頂点3と4のこのグラフ上に線形コンパートメントモデルを作成できます。

```jldoctest
julia> ode = linear_compartment_model([[2, 4], [1, 3], [2, 4], [1, 3]], outputs = [1], inputs = [2], leaks = [2, 3])
x1' = -x1*a_2_1 - x1*a_4_1 + x2*a_1_2 + x4*a_1_4
x3' = x2*a_3_2 - x3*a_2_3 - x3*a_4_3 - x3*a_0_3 + x4*a_3_4
x2' = x1*a_2_1 - x2*a_1_2 - x2*a_3_2 - x2*a_0_2 + x3*a_2_3 + u2
x4' = x1*a_4_1 + x3*a_4_3 - x4*a_1_4 - x4*a_3_4
y1 = x1
```
