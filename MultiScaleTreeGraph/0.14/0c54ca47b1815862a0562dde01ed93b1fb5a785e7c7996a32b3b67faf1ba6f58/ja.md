```
traverse!(node::Node, f::Function[, args...], <keyword arguments>)
traverse(node::Node, f::Function[, args...], <keyword arguments>)
```

ツリー内の任意の開始ノードを指定して（サブ）ツリーのノードをトラバースし、関数を適用します。この関数は変更を加えるもの（`traverse!`を使用）または変更を加えないもの（`traverse`を使用）です。

# 引数

  * `node::Node`: MTGノード（*例* `read_mtg()`によって返される全体のmtg）。
  * `f::Function`: 各ノードに適用する関数
  * `args::Any`: 関数に渡す任意の引数
  * <keyword arguments>:

      * `scale = nothing`: フィルタリングするスケール（保持するため）。通常は整数のタプルのようなもの。
      * `symbol = nothing`: フィルタリングするシンボル。通常は文字列のタプルのようなもの。
      * `link = nothing`: フィルタリングする前のノードとのリンク。通常は文字のタプルのようなもの。
      * `filter_fun = nothing`: ノードを入力として受け取る任意のフィルタリング関数、例：[`isleaf`](@ref)。
      * `all::Bool = true`: フィルタリングされたすべてのノードを返す（`true`）、または最初にフィルタリングされたノードで停止する（`false`）。
      * `type::Type = Any`: 返される配列の要素の型。これにより処理が高速化されることがあります。変更を加えないバージョンでのみ利用可能。
      * `recursivity_level::Int = Inf`: トラバースの最大深度。デフォルトは`Inf`（*例* 制限なし）。

# 戻り値

`traverse!`は（サブ）ツリーをインプレースで変更するため`nothing`を返し、`traverse`は`Array{type}`（または`type`が指定されていない場合は`Array{Any}`）を返します。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)
traverse!(mtg, node -> isleaf(node) ? println(node_id(node)," is a leaf") : nothing)
node_5 is a leaf
node_7 is a leaf

# 複雑な命令セットがある場合は、`do...end`ブロック記法を使用することもできます：
traverse!(mtg) do node
    if isleaf(node)
         println(node_id(x)," is a leaf")
    end
end
```
