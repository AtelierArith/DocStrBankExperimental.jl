TreeViewRoot(::String)

Create a TreeViewRoot for use as content in a TreeView widget

# Examples

Create a TreeViewRoot

```
    tree = TreeViewRoot()
    beverages = TreeViewNode("Beverages")
    push!(tree, beverages)
    push!(tree, TreeViewNode("Food"))
```

And push some children into a node if you want

```
    push!(beverages, TreeViewNode("Water"))
    push!(beverages, TreeViewNode("Tea"))
    push!(beverages, TreeViewNode("Coffee"))
```
