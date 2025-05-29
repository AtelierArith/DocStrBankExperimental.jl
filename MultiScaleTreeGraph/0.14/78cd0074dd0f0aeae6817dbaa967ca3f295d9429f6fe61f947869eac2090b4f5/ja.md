```
insert_parents!(node::Node, template, <キーワード引数>)
insert_generations!(node::Node, template, <キーワード引数>)
insert_children!(node::Node, template, <キーワード引数>)
insert_siblings!(node::Node, template, <キーワード引数>)
```

フィルタールールに従ってmtgに新しいノードを挿入します。関数は常にルートノードを返すことに注意することが重要です。古いノードであっても新しく挿入されたものであっても、ユーザーは結果をオブジェクトに割り当てることが推奨されます。

MTGにプログラム的にノードを挿入する方法：

  * フィルタリングされたノードの新しい親： `insert_parents!`
  * フィルタリングされたノードの新しい子： `insert_children!`
  * フィルタリングされたノードの新しい兄弟： `insert_siblings!`
  * フィルタリングされたノードの新しい子ですが、フィルタリングされたノードの以前の子は挿入されたノードの子になります： `insert_generations!`

# 引数

## 必須引数

  * `node::Node`: 開始するノード。
  * `template`:

      * 挿入されるノードに使用されるテンプレート [`NodeMTG`](@ref) または [`MutableNodeMTG`](@ref)
      * リンク、シンボル、インデックス、スケールの値を持つNamedTuple
      * または、ノードを入力として受け取り、前述のテンプレートを返す関数
  * `attr`: ノードの属性。`template`と同様に、次のようにすることができます：

      * ノード属性と同じ型の属性（*例*：DictまたはNamedTuple）
      * 新しい属性を計算する関数（属性の同じ型を返す必要があります）

## キーワード引数（フィルター）

  * `scale = nothing`: 挿入するスケール。通常は整数のタプルのようなもの。
  * `symbol = nothing`: 挿入するシンボル。通常は文字列のタプルのようなもの。
  * `link = nothing`: 挿入するリンク。通常はCharのタプルのようなもの。
  * `all::Bool = true`: 最初の挿入の後に続けるか（`true`）、停止するか。
  * `filter_fun = nothing`: ノードを入力として受け取る任意の関数、例： [`isleaf`](@ref) どのノードに基づいて挿入を行うかを決定します。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# スケール2のすべてのノードの前に新しいShootノードを挿入します：
mtg = insert_parents!(mtg, MultiScaleTreeGraph.MutableNodeMTG("/", "Shoot", 0, 1), scale = 2)

mtg
```
