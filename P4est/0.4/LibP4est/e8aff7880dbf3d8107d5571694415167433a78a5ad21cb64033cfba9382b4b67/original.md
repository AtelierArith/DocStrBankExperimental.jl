```
p6est_connectivity
```

This structure holds the 2D+1D inter-tree connectivity information. It is essentially a wrapper of the 2D p4est_connecitivity_t datatype, with some additional information about how the third dimension is embedded.

| Field        | Note                                                                                                                                          |
|:------------ |:--------------------------------------------------------------------------------------------------------------------------------------------- |
| conn4        | the 2D connecitvity; owned; vertices interpreted as the vertices of the bottom of the sheet                                                   |
| top_vertices | if NULL, uniform vertical profile, otherwise the vertices of the top of the sheet: should be the same size as *conn4*->tree*to*vertex; owned. |
| height       | if *top_vertices* == NULL, this gives the offset from the bottom of the sheet to the top                                                      |
