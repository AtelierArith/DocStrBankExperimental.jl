```
FileTree(parent, name, children, value)
```

#### Fields:

  * `parent::Union{FileTree, Nothing}` – The parent node. `nothing` if it's the root node.
  * `name::String` – Name of the root.
  * `children::Vector` – children
  * `value::Any` – the value at the node, if no value is present, a `NoValue()` sentinal value.

    FileTree(tree::FileTree; parent, name, children, value)

Copy over all fields from `tree`, but use any fields provided as keyword arguments.

```
FileTree(dirname::String)
```

Construct a `FileTree` to reflect directory from disk in the current working directory.
