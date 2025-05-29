```
t8_load_mode
```

This enumeration contains all modes in which we can open a saved cmesh. The cmesh can be loaded with more processes than it was saved and the mode controls, which of the processes open files and distribute the data.

| Enumerator     | Note                                                                                                                                                                                                                     |
|:-------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| T8_LOAD_SIMPLE | In simple mode, the first n processes load the file                                                                                                                                                                      |
| T8_LOAD_BGQ    | In BGQ mode, the file is loaded on n nodes and from one process of each node. This needs MPI Version 3.1 or higher.                                                                                                      |
| T8_LOAD_STRIDE | Every n-th process loads a file. Handle with care, we introduce it, since on Juqueen MPI-3 was not available. The parameter n has to be passed as an extra parameter.  # See also [`t8_cmesh_load_and_distribute`](@ref) |
| T8_LOAD_COUNT  |                                                                                                                                                                                                                          |
