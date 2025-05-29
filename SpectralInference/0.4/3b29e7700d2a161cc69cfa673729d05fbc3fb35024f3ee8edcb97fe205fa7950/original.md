```
spectral_lineage_encoding(tree::Node, orderedleafnames=getleafnames(tree); filterfun=x->true)
```

returns vector of named tuples with the id `nodeid` of the node and `sle` a vector of booleans ordered by `orderedleafnames` where true indicates the leaf descends from the node and false indicates that it does not.
