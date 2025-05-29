```
t8_cmesh_trees_set_all_boundary(cmesh, trees)
```

Set all neighbor fields of all local trees and ghosts to boundary.

# Arguments

  * `cmesh,`:[in,out] The associated cmesh.
  * `trees,`:[in,out] The trees structure. A face f of tree t counts as boundary if the face-neighbor is also t at face f.

### Prototype

```c
void t8_cmesh_trees_set_all_boundary (t8_cmesh_t cmesh, t8_cmesh_trees_t trees);
```
