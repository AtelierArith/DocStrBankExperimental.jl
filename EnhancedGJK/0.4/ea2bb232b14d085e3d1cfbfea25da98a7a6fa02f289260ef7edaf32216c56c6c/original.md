The NeighborMesh is what actually makes EnhancedGJK "enhanced". It consists of a mesh and a pre-computed set of neighbors for each vertex. These neighbors will be searched when the GJK simplex is refined. Searching over just the neighbors of a particular vertex allows us to avoid repeatedly searching over every vertex in the mesh.

Note that constructing a new NeighborMesh is expensive (and unoptimized). We recommend constructing the NeighborMesh for each of your meshes ahead of time.
