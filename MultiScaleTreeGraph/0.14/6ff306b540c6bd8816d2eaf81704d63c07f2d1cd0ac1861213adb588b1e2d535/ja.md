delete_nodes!(mtg::Node,<keyword arguments>)

フィルタールールに従ってmtg内のノードを削除します。

# 引数

## 必須引数

  * `node::Node`: 開始するノード。

## キーワード引数（フィルタ）

  * `scale = nothing`: 削除するスケール。通常は整数のタプルのようなもの。
  * `symbol = nothing`: 削除するシンボル。通常は文字列のタプルのようなもの。
  * `link = nothing`: 削除する前のノードとのリンク。通常はCharのタプルのようなもの。
  * `all::Bool = true`: 最初の削除の後に続けるか（`true`）、それとも停止するか？
  * `filter_fun = nothing`: ノードを入力として受け取る任意のフィルタリング関数、例：[`isleaf`](@ref)

ノードを削除するかどうかを決定します。

  * `child_link_fun = new_child_link`: 削除されたノードの子ノードを入力として受け取り、その新しいリンクを返す関数（詳細は下記参照）。

# 注意事項

1. この関数はアクロペタルであり、葉から根に向かって削除を適用します。これにより、一度のパスで十分であり、すでに訪れた子ノードを再訪するプロセスを繰り返すことはありません。
2. この関数は特別なことはせず、ノードを削除する際のルールはユーザーに任せます。ただし、リンクについては例外です（下記参照）。
3. パッケージはフィルタリングのためのいくつかの事前作成された関数を提供します。例えば、[`is_segment!`](@ref)を参照して、特定のスケールでmtgを再計算し、分岐点にのみノードを持つようにします。これは、*e.g.* LiDARポイントクラウドからの自動再構築と手動測定を一致させるためにしばしば使用されます。
4. `child_link_fun`に使用されるデフォルト関数は[`new_child_link`](@ref)であり、親と子のリンクを考慮して賢くなろうとします。詳細についてはそのヘルプページを参照してください。リンクを変更する必要がない場合は、代わりに`link`関数を使用してください。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

delete_nodes!(mtg, scale = 2) # スケール2のすべてのノードを削除します

# 葉を削除：
delete_nodes!(mtg, symbol = "Leaf")
# 葉と内部ノードを削除：
delete_nodes!(mtg, symbol = ("Leaf","Internode"))
```
