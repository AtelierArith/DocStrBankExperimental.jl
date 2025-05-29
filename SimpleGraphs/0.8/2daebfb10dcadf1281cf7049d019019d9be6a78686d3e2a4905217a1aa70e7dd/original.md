`faces(G::UndirectedGraph)` returns the set of faces of this graph  (given its rotation system). The rotation system is a  planar embedding iff this returns `2`.

Each face is a `RingList` of the (directed) edges bordering the face.

*Requires that the graph is connected and has at least one edge.*
