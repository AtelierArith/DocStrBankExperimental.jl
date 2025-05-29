```
t8_cmesh_set_dimension(cmesh, dim)
```

Set the dimension of a cmesh. If any tree is inserted to the cmesh via [`t8_cmesh_set_tree_class`](@ref), then the dimension is set automatically to that of the inserted tree. However, if the cmesh is constructed partitioned and the part on this process is empty, it is necessary to set the dimension by hand.

# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `dim`:[in] The dimension to be set. Must satisfy 0 <= dim <= 3. The cmesh must not be committed before calling this function.

### Prototype

```c
void t8_cmesh_set_dimension (t8_cmesh_t cmesh, int dim);
```
