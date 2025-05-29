```
descendants(node::Node,key,<keyword arguments>)
descendants(node::Node,<keyword arguments>)
descendants!(node::Node,key,<keyword arguments>)
```

ノードの子孫から属性値を取得します（アクロペタル）。最初のメソッドは値の配列を返し、2番目はフィルターを尊重するノードの配列を返し、3番目は結果をmtgにキャッシュする最初のメソッドの変更版です。

変更版（`descendants!`）は、関数呼び出しのハッシュにちなんで名付けられたキャッシュ変数に結果をキャッシュします。このバージョンは、大きな木に対して同じ計算のために`descendants`が繰り返し呼び出されるときに非常に速くなりますが、時々キャッシュをクリアする必要があります（[`clean_cache!`](@ref)を参照）。また、`AbstractDict`のサブタイプの属性を持つ木にのみ機能します。

# 引数

## 必須引数

  * `node::Node`: 開始するノード。
  * `key`: キーまたは属性名（最初と3番目のメソッドにのみ必須）。計算時間を短縮するために`Symbol`にしてください。

## キーワード引数

  * `scale = nothing`: フィルタリングするスケール（保持するため）。通常は整数のタプルのようなものです。
  * `symbol = nothing`: フィルタリングするシンボル。通常は文字列のタプルのようなものです。
  * `link = nothing`: フィルタリングする前のノードとのリンク。通常は文字のタプルのようなものです。
  * `all::Bool = true`: フィルタリングされたすべてのノードを返すか（`true`）、フィルタリングされていない最初のノードで停止するか（`false`）。
  * `self = false`: 現在のノードの値が必要ですか？
  * `filter_fun = nothing`: ノードを入力として受け取る任意のフィルタリング関数、例：[`isleaf`](@ref)。
  * `recursivity_level = Inf`: 許可される最大再帰数（フィルターを考慮）。

*例*：最初のレベルの子供のみを取得するには：`recursivity_level = 1`、子供 + 孫を取得するには：`recursivity_level = 2`。`Inf`（デフォルト）または負の値が提供されると、再帰の制限はありません。

  * `ignore_nothing = false`: 指定された`key`の`nothing`値を持つノードをフィルタリングします。
  * `type::Union{Union,DataType}`: 属性の型。提供されると関数がはるかに速く実行される可能性があります（*例*：約4倍速）。

# ヒント

葉の値を取得するには、フィルタリング関数として[`isleaf`](@ref)を使用します。例：`descendants(mtg, :Width; filter_fun = isleaf)`。

# 注意

ほとんどの場合、`type`引数は`Nothing`と属性のデータ型のユニオンとして指定する必要があります。これは、欠損または存在しないデータを管理するためです。例：1つのスケールでのみ行われた測定。詳細については例を参照してください。

# 例

```julia
# GitHubリポジトリからmtgをインポート：
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

descendants(mtg, :Length) # 短く書けるが、実行は遅い

# 高速バージョン。`Length`属性を持たないノードがあるため、`Nothing`とFloat64のユニオンを渡します：
descendants(mtg, :Length, type = Union{Nothing,Float64})

# スケールでフィルタリング：
descendants(mtg, :XEuler, scale = 3, type = Union{Nothing, Float64})
descendants(mtg, :Length, scale = 3, type = Float64) # ここには`nothing`値はないので、ユニオン型は不要

# シンボルでフィルタリング：
descendants(mtg, :Length, symbol = "Leaf")
descendants(mtg, :Length, symbol = ("Leaf","Internode"))

# 関数でフィルタリング。例：葉の値のみを取得：
descendants(mtg, :Width; filter_fun = isleaf)

# 異なる属性をベクターとして渡すこともできます：
descendants(mtg, [:Width, :Length]; filter_fun = isleaf)
# 出力は、要求した属性の長さの配列の配列です。

# 変更版`descendants!`を使用してmtgに結果をキャッシュすることも可能です（関数名の末尾の`!`に注意）：
transform!(mtg, node -> sum(descendants!(node, :Length)) => :subtree_length, symbol = "Internode")

# または、`transform!`の代わりに`@mutate_mtg!`を使用：
@mutate_mtg!(mtg, subtree_length = sum(descendants!(node, :Length)), symbol = "Internode")

# キャッシュは、関数呼び出しのSHAに続く名前で始まる一時変数に保存されます。
# 例：`:_cache_5c1e97a3af343ce623cbe83befc851092ca61c8d`：
node_attributes(mtg[1][1][1])

# メモリを使いすぎないようにキャッシュをクリアすることもできます：
clean_cache!(mtg)
node_attributes(mtg[1][1][1])
```
