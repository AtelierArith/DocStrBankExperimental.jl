```
node_mtg(node::Node)
```

Get the MTG encoding of the node, *i.e.* the MTG description (see [`NodeMTG`](@ref) or [`MutableNodeMTG`](@ref)):

  * `scale`: the scale of the node (*e.g.* 1)
  * `symbol`: the symbol of the node (*e.g.* "Axis")
  * `index`: the index of the node (*e.g.* 1, this is free)
  * `link`: the link of the node ("/", "+" or "<")
