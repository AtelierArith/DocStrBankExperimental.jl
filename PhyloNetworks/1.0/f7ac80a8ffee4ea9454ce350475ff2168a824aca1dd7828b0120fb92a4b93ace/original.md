```
printedges(net)
printedges(io::IO, net)
```

Print information on the edges of a `HybridNetwork` `net`: edge number, numbers of nodes attached to it, edge length, whether it's a hybrid edge, its γ inheritance value, whether it's a major edge, if it could contain the root (this field is not always updated, though) and one more attribute pertaining to level-1 networks used in SNaQ: in which cycle it is contained (-1 if no cycle).
