```
insert_parent!(node, template, attr_fun = node -> typeof(node_attributes(node))(), max_id = [max_id(node)])
insert_generation!(node, template, attr_fun = node -> typeof(node_attributes(node))(), max_id = [max_id(node)])
insert_child!(node, template, attr_fun = node -> typeof(node_attributes(node))(), max_id = [max_id(node)])
insert_sibling!(node, template, attr_fun = node -> typeof(node_attributes(node))(), max_id = [max_id(node)])
```

MTGにノードを挿入するには：

  * ノードの新しい親として： `insert_parent!`
  * ノードの新しい子として： `insert_child!`
  * ノードの新しい兄弟として： `insert_sibling!`
  * ノードの新しい子として、ただしノードの子は挿入されたノードの子になる：

`insert_generation!`

# 引数

  * `node::Node`: ノードを挿入するノード（親、子、または兄弟として）。
  * `template`:

      * 挿入されるノードに使用されるテンプレート [`NodeMTG`](@ref) または [`MutableNodeMTG`](@ref)
      * リンク、シンボル、インデックス、スケールの値を持つ NamedTuple
      * またはノードを入力として受け取り、前述のテンプレートを返す関数
  * `attr_fun`: フィルタリングされたノードに基づいて新しい属性を計算する関数。次のように返す必要があります。

MTGの他のノードで使用されるものと同じ型の属性値（*例*：DictまたはNamedTuple）。ノードに属性値を渡すだけが必要な場合は `x -> your_values` を使用してください。

  * `max_id::Vector{Int64}`: MTG内のノードの最大IDを長さ1のベクトルとして表します。関数内でインクリメントされ、

デフォルトでは [`max_id`](@ref) の値を使用します。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

template = MultiScaleTreeGraph.MutableNodeMTG("/", "Shoot", 0, 1)
insert_parent!(mtg[1][1], template)
mtg

# テンプレートはテンプレートを返す関数であることもできます。たとえば、ダミーの例は
# ノードの最初の子の NodeMTG を使用する関数です：

insert_parent!(
    mtg[1][1],
    node -> (
        link = link(node[1]),
        symbol = symbol(node[1]),
        index = index(node[1]),
        scale = scale(node[1]))
    )
)
```
