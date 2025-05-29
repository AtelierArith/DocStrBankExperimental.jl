```
cref=add_sum!(graph,node,c,nodelist,base_name=node)
```

Adds a linear combination of more than two nodes, given in `nodelist::Vector`, with coefficients given in `c`. The `base_name` is temporary variables for the summing. The sum is stored in `node`.

Returns `cref` list with references.
