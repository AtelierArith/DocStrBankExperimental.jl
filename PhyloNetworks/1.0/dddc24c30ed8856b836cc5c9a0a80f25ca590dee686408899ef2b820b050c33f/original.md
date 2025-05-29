```
printnodes(net)
printnodes(io, net)
```

Print information on the nodes of a `HybridNetwork` net: node number, whether it's a leaf, whether it's a hybrid node, it's name (label), its `intn1` field (for level-1 networks in SNaQ: number given to the cycle in which the node might be, -1 if the node it *not* in a cycle cycle), and the list of edges attached to it, by their numbers.
