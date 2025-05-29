TreeView(::TreeViewRoot)

TreeViewRoot構造体からTreeViewウィジェットを作成します

# 例

TreeViewを作成する

```
    tree = TreeViewRoot()
    beverages = TreeViewNode("飲み物")
    push!(beverages, TreeViewNode("水"))
    push!(beverages, TreeViewNode("お茶"))
    push!(tree, beverages)
    push!(tree, TreeViewNode("食べ物"))

    treeview = TreeView(tree)
```

要素のObservable選択を取得するには:

```
    treeview[]
```
