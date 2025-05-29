```
EdgeT{node type}
Edge = EdgeT{Node}
Edge(number, length=1.0)
```

Data structure for an edge and its various attributes. Most notably:

  * `number` (integer): serves as unique identifier; remains unchanged when the network is modified, with a nearest neighbor interchange for example
  * `node`: vector of [`Node`](@ref)s, normally just 2 of them
  * `ischild1` (boolean): `true` if `node[1]` is the child node of the edge, false if `node[1]` is the parent node of the edge
  * `length`: branch length
  * `hybrid` (boolean): whether the edge is a tree edge or a hybrid edge (in which case `ischild1` is important, even if the network is semi-directed)
  * `gamma`: proportion of genetic material inherited by the child node via the edge; 1.0 for a tree edge
  * `ismajor` (boolean): whether the edge is the major path to the child node; `true` for tree edges, since a tree edge is the only path to its child node; normally true if `gamma>0.5`.
  * `containroot` (boolean): is the interior of this edge a valid rooting position? That is, if we added a node on the edge, could we direct all edges away from this new node to root the semidirected network and get a valid rooted network?

and other fields, used very internally
