```
update_ϕ!(::ComputationRound, ::ComputationQubit, ::InputQubits, meta_graph, vertex)
```

指定された頂点の `meta_graph` 内の ϕ 値を計算ラウンド中に計算キュービットと入力キュービットを使用して更新します。新しい ϕ 値は、初期キュービット、秘密の角度、古典的入力、X 補正、および Z 補正を含む頂点のいくつかの特性に基づいて計算されます。

# 引数

  * `::ComputationRound`: この関数が計算ラウンド中に使用されることを示します。
  * `::ComputationQubit`: 計算キュービットが使用されることを示します。
  * `::InputQubits`: 入力キュービットが存在することを示します。
  * `meta_graph`: 更新されるグラフ。
  * `vertex`: ϕ 値を更新するグラフ内の頂点。

# 戻り値

  * 更新された `meta_graph`。

# 例

```julia
updated_graph = update_ϕ!(ComputationRound(), ComputationQubit(), InputQubits(), meta_graph, vertex) # グラフ内の指定された頂点の ϕ 値を更新します
```
