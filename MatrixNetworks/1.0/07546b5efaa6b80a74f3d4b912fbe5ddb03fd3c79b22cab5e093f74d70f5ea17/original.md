# `chung_lu_undirected`

Generate an approximate undirected Chung-Lu graph. The approximation is because we draw exactly |E| edges where each edge is sampled from the Chung-Lu model. But then we discard duplicate edges and self-loops. So the new graph will always have fewer edges than the input degree sequence.

**This will likely change in future versions and provide an exact Chung-Lu model.**

If the graph is 

## Usage

  * `chung_lu_undirected(d)`
  * `chung_lu_undirected(d,nedges)`

## Input

  * `d`: the degree sequence vector. This vector is non-negative and has the expected

degree for each vertex.

## Output

  * A MatrixNetwork for the undirected graph that results from the Chung-Lu sample.

## Example

```
A = load_matrix_network("tapir")
d = vec(sum(A,1))
B = sparse(chung_lu_undirected(d))
nnz(A)
nnz(B)
```
