# `is_empty`

Return true if the graph is the empty graph and  false otherwise. 

## Functions

-`is_empty(A::MatrixNetwork)`

## Example

```
is_empty(MatrixNetwork(Int[],Int[],0))
is_empty(erdos_renyi_undirected(0,0))
```
