```
ancestors(node::Node,key,<keyword arguments>)
ancestors(node::Node,<keyword arguments>)
```

祖先（基底方向）から属性値を取得するか、フィルタリングされていない祖先ノードを取得します。

# 引数

## 必須引数

  * `node::Node`: 開始するノード。
  * `key`: キーまたは属性名。属性値を検索する最初のメソッドにのみ必須です。2番目のメソッドはノードを直接返します。

計算時間を短縮するために`Symbol`にしてください。

## キーワード引数

  * `scale = nothing`: フィルタリングするスケール（保持するため）。通常は整数のタプルのようなものです。
  * `symbol = nothing`: フィルタリングするシンボル。通常は文字列のタプルのようなものです。
  * `link = nothing`: フィルタリングする前のノードとのリンク。通常は文字のタプルのようなものです。
  * `all::Bool = true`: フィルタリングされたすべてのノードを返すか（`true`）、フィルタリングされた最初のノードで停止するか（`false`）。
  * `self = false`: 現在のノードの値が必要ですか？
  * `filter_fun = nothing`: ノードを入力として受け取る任意のフィルタリング関数、例：[`isleaf`](@ref)。
  * `recursivity_level = -1`: 許可される再帰の最大数（フィルタを考慮）。

*例*：親のみを取得するには：`recursivity_level = 1`、親 + 祖父母の場合：`recursivity_level = 2`。負の値が提供された場合（デフォルト）、関数はノードからルートまでのすべての有効な値を返します。

  * `ignore_nothing = false`: 指定された`key`の`nothing`値を持つノードをフィルタリングします。
  * `type::Union{Union,DataType}`: 属性の型。提供されると関数がはるかに速く実行されます（約4倍速）。

# 注意

ほとんどの場合、`type`引数は`Nothing`と属性のデータ型のユニオンとして指定する必要があります。これにより、欠損または存在しないデータを管理できます。例えば、1つのスケールでのみ行われた測定など。詳細については例を参照してください。

# 例

```julia
# パッケージからの例のmtgをインポート：
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# mtgからの葉ノードを使用：
leaf_node = get_node(mtg, 5)

ancestors(leaf_node, :Length) # 書きやすいが、実行は遅い

# 高速バージョン、`Length`属性がないノードがあるため、NothingとFloat64のユニオンを渡します：
ancestors(leaf_node, :Length, type = Union{Nothing,Float64})

# スケールでフィルタリング：
ancestors(leaf_node, :XX, scale = 1, type = Float64)
ancestors(leaf_node, :Length, scale = 3, type = Float64)

# シンボルでフィルタリング：
ancestors(leaf_node, :Length, symbol = "Internode")
ancestors(leaf_node, :Length, symbol = ("Axis","Internode"))
```
