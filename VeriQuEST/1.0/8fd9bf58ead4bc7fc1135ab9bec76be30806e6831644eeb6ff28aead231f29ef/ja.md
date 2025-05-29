```
update_ϕ!(::MBQC, ::ComputationQubit, qT::Union{NoInputQubits,InputQubits}, meta_graph, vertex)
```

指定された頂点のϕ値を、計算キュービットと入力キュービットがない場合または入力キュービットがある場合の測定ベース量子計算（MBQC）モデルの計算ラウンド中に`meta_graph`で更新します。新しいϕ値は、頂点の秘密の角度、X補正、Z補正など、いくつかの特性に基づいて計算されます。

# 引数

  * `::MBQC`: この関数がMBQCモデルで使用されることを示します。
  * `::ComputationQubit`: 計算キュービットが使用されることを示します。
  * `qT::Union{NoInputQubits,InputQubits}`: 入力キュービットがない場合または入力キュービットがあることを示します。
  * `meta_graph`: 更新されるグラフ。
  * `vertex`: ϕ値を更新するグラフ内の頂点。

# 戻り値

  * 更新された`meta_graph`。

# 例

```julia
updated_graph = update_ϕ!(MBQC(), ComputationQubit(), NoInputQubits(), meta_graph, vertex) # グラフ内の指定された頂点のϕ値を更新します
updated_graph = update_ϕ!(MBQC(), ComputationQubit(), InputQubits(), meta_graph, vertex) # グラフ内の指定された頂点のϕ値を更新します
```
