```
NodeMTG(link, symbol, index, scale)
MutableNodeMTG(link, symbol, index, scale)
```

# NodeMTG structure

Builds an MTG node to hold data about the link to the previous node, the symbol of the node, and its index.

# Note

  * The symbol should match the possible values listed in the `SYMBOL` column of the `CLASSES` section

in the mtg file if read from a file.

  * The index is totaly free, and can be used as a way to *e.g.* keep track of the branching order.

```julia
NodeMTG("<", "Leaf", 2, 0)
```
