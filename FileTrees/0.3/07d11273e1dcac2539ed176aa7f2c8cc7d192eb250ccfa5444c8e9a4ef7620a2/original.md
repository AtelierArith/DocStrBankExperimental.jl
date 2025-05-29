```
File(parent, name, value=NoValue())
```

#### Fields:

  * `parent::Union{FileTree, Nothing}` – The parent node. `nothing` if it's the root node.
  * `name::String` – Name of the root.
  * `value::Any` – the value at the node, if no value is present, a `NoValue()` sentinal value.
