# `random_edge`

Identify a random edge of a matrix network or sparse matrix.

## Functions

  * `random_edge(A::MatrixNetwork) -> (ei,ej,ind)`   gets a random edge/non-zero from the matrix
  * `random_edge(A::SparseMatrixCSC) -> (ei,ej,ind)`   gets a random non-zero from the matrix

## Example

```
G = lollipop_graph(5,3)
# count the number of edges we randomly see between the regions
C = Dict{Symbol,Int}()
M = zeros(8,8)
for i=1:1000000
  ei,ej = MatrixNetwork.random_edge(G)
  M[ei,ej] += 1
  if 1 <= ei <= 5 && 1 <= ej <= 5
    C[:Stem] = get(C, :Stem, 0) + 1
  elseif 6 <= ei <= 10 && 6 <= ej <= 10
    C[:Pop] = get(C, :Pop, 0) + 1  
  else
    C[:Bridge] = get(C, :Bridge, 0) + 1  
  end
end
# 4 edges in stem, 3 edges in pop, 1 edge in bridge 
@show C
@show M
```
