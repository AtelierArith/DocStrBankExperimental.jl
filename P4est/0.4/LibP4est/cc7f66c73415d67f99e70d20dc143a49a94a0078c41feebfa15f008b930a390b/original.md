```
p8est_ghost_t
```

quadrants that neighbor the local domain

| Field                     | Note                                                                                                                      |
|:------------------------- |:------------------------------------------------------------------------------------------------------------------------- |
| btype                     | which neighbors are in the ghost layer                                                                                    |
| ghosts                    | array of [`p8est_quadrant_t`](@ref) type                                                                                  |
| tree_offsets              | num_trees + 1 ghost indices                                                                                               |
| proc_offsets              | mpisize + 1 ghost indices                                                                                                 |
| mirrors                   | array of [`p8est_quadrant_t`](@ref) type                                                                                  |
| mirror_tree_offsets       | num_trees + 1 mirror indices                                                                                              |
| mirror_proc_mirrors       | indices into mirrors grouped by outside processor rank and ascending within each rank                                     |
| mirror_proc_offsets       | mpisize + 1 indices into  mirror_proc_mirrors                                                                             |
| mirror_proc_fronts        | like mirror_proc_mirrors, but limited to the outermost octants. This is NULL until [`p8est_ghost_expand`](@ref) is called |
| mirror_proc_front_offsets | NULL until [`p8est_ghost_expand`](@ref) is called                                                                         |
