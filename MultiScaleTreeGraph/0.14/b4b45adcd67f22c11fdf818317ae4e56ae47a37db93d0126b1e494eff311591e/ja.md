```
@mutate_mtg!(node, args...,kwargs...)
```

MTGノードをその場で変更します。

# 引数

  * `mtg`: 変更するMTG
  * `args...`: ノードに適用する計算（例を参照）
  * `kwargs...`: 遷移およびフィルタリングのためのオプションのキーワード引数（詳細を参照）

# 詳細

[`descendants`](@ref)および[`ancestors`](@ref)と同様に、kwargsは以下のいずれかのフィルタを指定できます：

  * `scale = nothing`: フィルタインするスケール（保持するため）。通常は整数のタプルのようなものです。
  * `symbol = nothing`: フィルタインするシンボル。通常は文字列のタプルのようなものです。
  * `link = nothing`: フィルタインする前のノードとのリンク。通常は文字のタプルのようなものです。
  * `all::Bool = true`: フィルタインされたすべてのノードを返す（`true`）、または最初にフィルタアウトされたノードで停止する（`false`）。
  * `filter_fun = nothing`: ノードを入力として受け取る任意のフィルタリング関数、例：[`isleaf`](@ref)。
  * `traversal`: 木の遷移のタイプ。デフォルトでは`AbstractTrees.PreOrderDFS`を使用します。

# 例

```julia
# パッケージからMTGをインポートする：
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# スケールを使って新しい属性を計算し、その値に2を加えます：
@mutate_mtg!(mtg, scaling = node.scales .+ 2, filter_fun = node -> node.scales !== nothing)

# 他の属性に基づいていくつかの新しい属性を計算します：
@mutate_mtg!(mtg, x = length(node_id(node)), y = node.x + 2, z = sum(node.y))

# 括弧なしでも使用できます：

@mutate_mtg! mtg x = length(node_id(node))
```
