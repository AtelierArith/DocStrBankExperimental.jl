# `preferential_attachment_graph`

Generate an instance of a preferential attachment graph. This is an undirected graph that is generated as follows:

  * Start with a k0-node clique.
  * Add n-k0 vertices where     each vertex links to k nodes chosen    based their degree (and repeats    are allowed).

## Functions

The following functions are synonyms

  * `preferential_attachment_graph`
  * `pa_graph`

and

  * `preferential_attachment_edges!`
  * `pa_edges!`

The computational functions are

  * `pa_graph(n,k,k0)` Generate a PA graph with a k0 node clique and n total nodes and k edges added per node. This returns a MatrixNetwork type

The edge functions are

  * `pa_edges!(nnew,k,edges)` Add new edges to an  existing set by adding `nnew` nodes to the set of edges where each node picks k edges based on the degrees. The new node ids are based on the largest entry in the edges array.
  * `pa_edges!(nnew,k,edges,n0)` Generate a set of edges total` nodes to the set of edges where n0+1 is the starting index for the new set of nodes

## Input

  * `n`: the number of nodes in the final graph
  * `k`: the number of links picked by each node when it is added. The actual degree can be larger or smaller than this number because of links from other nodes or duplicates selected.
  * `k0`: The number of nodes in the starting clique.
  * `edges`: A list of edges to be manipulated in the process of

generating new edges. 

## Output

  * A matrix network type for the preferential attachment graph.
  * `edges` An updated list of edges.

## Example

```
pa_graph(100,5,2)
```
