TreeViewRoot(::String)

TreeViewウィジェットのコンテンツとして使用するTreeViewRootを作成します

# 例

TreeViewRootを作成する

```
    tree = TreeViewRoot()
    beverages = TreeViewNode("飲み物")
    push!(tree, beverages)
    push!(tree, TreeViewNode("食べ物"))
```

必要に応じてノードに子を追加します

```
    push!(beverages, TreeViewNode("水"))
    push!(beverages, TreeViewNode("お茶"))
    push!(beverages, TreeViewNode("コーヒー"))
```
