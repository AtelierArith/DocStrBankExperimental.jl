# `roach_graph`

Generate a roach graph on 4n vertices which follows the Guattery-Miller  description. The roach graph has a body that consists of 2n vertices which ard two n-vertex line-graphs that have been connected together. The body has two antennae that result from adding an n-vertex line graph  to one vertex on each side. 

```
# the graph looks like
#
# (           top body               )   (       top antennae       )    
#
# o - o - o - ... n vertices total - o - o - ... n vertices total - 0
# |   |   |   ...    |   |   |   |   |
# o - o - o - ... n vertices total - o - o - ... n vertices total - 0
#
# (         bottom body              )   (     bottom antennae      )
#
# there are 4n vertices and 2(2n-1) + n edges
```

## Functions

  * `roach_graph(n) -> A::MatrixNetwork`
  * `roach_graph(n, Val{true}) -> (A::MatrixNetwork, Matrix{Float64})` this also returns coordinates for the graph.

## Example

```
A = sparse_transpose(roach_graph(3, Val{true})) # get back the matrix 
L = spdiagm(vec(sum(A,2))) - A

#lams,vecs = eig(full(L))

```
