```
update_ϕ!(::TestRound, ::TrapQubit, ::NoInputQubits, meta_graph, vertex)
```

指定された頂点の `meta_graph` 内の ϕ 値を、トラップキュービットと入力キュービットなしのテストラウンド中に更新します。新しい ϕ 値は、初期キュービット θᵥ とランダムに引かれた rᵥ 値に基づいて計算されます。

# 引数

  * `::TestRound`: この関数がテストラウンド中に使用されることを示します。
  * `::TrapQubit`: トラップキュービットが使用されることを示します。
  * `::NoInputQubits`: 入力キュービットがないことを示します。
  * `meta_graph`: 更新されるグラフ。
  * `vertex`: ϕ 値を更新するグラフ内の頂点。

# 戻り値

  * 更新された `meta_graph`。

# 例

```julia
updated_graph = update_ϕ!(TestRound(), TrapQubit(), NoInputQubits(), meta_graph, vertex) # グラフ内の指定された頂点の ϕ 値を更新します
```
