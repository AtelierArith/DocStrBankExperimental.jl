```
update_ϕ!(::ComputationRound, ::ComputationQubit, ::NoInputQubits, meta_graph, vertex)
```

指定された頂点の `meta_graph` 内の ϕ 値を、計算キュービットと入力キュービットなしで計算ラウンド中に更新します。新しい ϕ 値は、初期キュービット、秘密の角度、X 補正、Z 補正など、頂点のいくつかの特性に基づいて計算されます。

# 引数

  * `::ComputationRound`: この関数が計算ラウンド中に使用されることを示します。
  * `::ComputationQubit`: 計算キュービットが使用されることを示します。
  * `::NoInputQubits`: 入力キュービットがないことを示します。
  * `meta_graph`: 更新されるグラフ。
  * `vertex`: ϕ 値を更新するグラフ内の頂点。

# 戻り値

  * 更新された `meta_graph`。

# 例

```julia
updated_graph = update_ϕ!(ComputationRound(), ComputationQubit(), NoInputQubits(), meta_graph, vertex) # グラフ内の指定された頂点の ϕ 値を更新します
```
