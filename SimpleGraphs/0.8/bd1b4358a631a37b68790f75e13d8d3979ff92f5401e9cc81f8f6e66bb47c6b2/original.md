`get_rot(G::UndirectedGraph,v)` returns a `RingList` of the neighbors of `v`. This assumes that `G` has an associate rotation system.

`get_rot(G::UndirectedGraph)` returns a copy of the rotation system  associated with `G`. If there is none, a rotation system will  be created for this graph. If the graph has an embedding,  that will be used to create the rotation system.
