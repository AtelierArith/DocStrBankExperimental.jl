TreeView(::TreeViewRoot)

Create a TreeView widget from a TreeViewRoot structure

# Examples

Create a TreeView

```
    tree = TreeViewRoot()
    beverages = TreeViewNode("Beverages")
    push!(beverages, TreeViewNode("Water"))
    push!(beverages, TreeViewNode("Tea"))
    push!(tree, beverages)
    push!(tree, TreeViewNode("Food"))

    treeview = TreeView(tree)
```

To get the Observable selection of elements:

```
    treeview[]
```
