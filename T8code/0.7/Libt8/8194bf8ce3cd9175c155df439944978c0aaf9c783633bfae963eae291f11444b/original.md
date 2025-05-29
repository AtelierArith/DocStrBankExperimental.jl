```
t8_cmesh
```

This structure holds the connectivity data of the coarse mesh. It can either be replicated, then each process stores a copy of the whole mesh, or partitioned. In the latter case, each process only stores a local portion of the mesh plus information about ghost elements.

The coarse mesh is a collection of coarse trees that can be identified along faces. TODO: this description is outdated. rewrite it. The array ctrees stores these coarse trees sorted by their (global) tree_id. If the mesh if partitioned it is partitioned according to an (possible only virtually existing) underlying fine mesh. Therefore the ctrees array can store duplicated trees on different processes, if each of these processes owns elements of the same tree in the fine mesh.

Each tree stores information about its face-neighbours in an array of t8*ctree*fneighbor.

If partitioned the ghost trees are stored in a hash table that is backed up by an array. The hash value of a ghost tree is its tree_id modulo the number of ghosts on this process.

| Field                      | Note                                                                                                                                                                                                              |
|:-------------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| committed                  | Flag that specifies whether the cmesh is committed or not. t8*cmesh*commit                                                                                                                                        |
| dimension                  | The dimension of the cmesh. It is set when the first tree is inserted.                                                                                                                                            |
| set_partition              | If nonzero the cmesh is partitioned. If zero each process has the whole cmesh.                                                                                                                                    |
| face_knowledge             | If partitioned the level of face knowledge that is expected. t8*mesh*set*partitioned; see t8*cmesh*set*partition.                                                                                                 |
| set_partition_scheme       | If the cmesh is to be partitioned according to a uniform level, the scheme that describes the refinement pattern. See t8*cmesh*set_partition.                                                                     |
| set_partition_level        | Non-negative if the cmesh should be partitioned from an already existing cmesh with an assumed *level* uniform mesh underneath.                                                                                   |
| set_from                   | If this cmesh shall be derived from an existing cmesh by copy or more elaborate modification, we store a pointer to this other cmesh here.                                                                        |
| mpirank                    | Number of this MPI process.                                                                                                                                                                                       |
| mpisize                    | Number of MPI processes.                                                                                                                                                                                          |
| rc                         | The reference count of the cmesh.                                                                                                                                                                                 |
| num_trees                  | The global number of trees                                                                                                                                                                                        |
| num_local_trees            | If partitioned the number of trees on this process.  Otherwise the global number of trees.                                                                                                                        |
| num_ghosts                 | If partitioned the number of neighbor trees owned by different processes.                                                                                                                                         |
| num_local_trees_per_eclass | After commit the number of local trees for each eclass. Stores the same entries as *num*trees*per_eclass*, if the cmesh is replicated.                                                                            |
| num_trees_per_eclass       | After commit the number of global trees for each eclass.                                                                                                                                                          |
| trees                      | structure that holds all local trees and ghosts                                                                                                                                                                   |
| first_tree                 | The global index of the first local tree on this process.  Zero if the cmesh is not partitioned. -1 if this processor is empty. See also https://github.com/DLR-AMR/t8code/wiki/Tree-indexing                     |
| first_tree_shared          | If partitioned true if the first tree on this process is also the last tree  on the next process. Always zero if num_local_trees = 0                                                                              |
| tree_offsets               | If partitioned for each process the global index of its first local tree or -(first local tree) - 1 if the first tree on that process is shared. Since this is very memory consuming we only fill it when needed. |
| geometry_handler           | Handles all geometries that are used by trees in this cmesh.                                                                                                                                                      |
| stash                      | Used as temporary storage for the trees before commit.                                                                                                                                                            |
| profile                    | Used to measure runtimes and statistics of the cmesh algorithms.                                                                                                                                                  |

# See also

t8_ctree_fneighbor
