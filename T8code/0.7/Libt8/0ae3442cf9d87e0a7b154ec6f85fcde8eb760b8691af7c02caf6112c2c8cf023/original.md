This structure holds the connectivity data of the coarse mesh. It can either be replicated, then each process stores a copy of the whole mesh, or partitioned. In the latter case, each process only stores a local portion of the mesh plus information about ghost elements.

The coarse mesh is a collection of coarse trees that can be identified along faces. TODO: this description is outdated. rewrite it. The array ctrees stores these coarse trees sorted by their (global) tree_id. If the mesh if partitioned it is partitioned according to an (possible only virtually existing) underlying fine mesh. Therefore the ctrees array can store duplicated trees on different processes, if each of these processes owns elements of the same tree in the fine mesh.

Each tree stores information about its face-neighbours in an array of t8*ctree*fneighbor.

If partitioned the ghost trees are stored in a hash table that is backed up by an array. The hash value of a ghost tree is its tree_id modulo the number of ghosts on this process.

# See also

t8_ctree_fneighbor
