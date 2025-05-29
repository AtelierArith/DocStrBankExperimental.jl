```
t8_cmesh_trees_copy_part(trees_dest, part_dest, trees_src, part_src)
```

Copy the trees array from one part to another.

# Arguments

  * `trees_dest`:[in,out] The trees struct of the destination part.
  * `part_dest`:[in] The index of the destination part. Must be initialized by t8*cmesh*trees*start*part with alloc = 0.
  * `trees_src`:[in] The trees struct of the source part.
  * `part_src`:[in] The index of the destination part. Must be a valid part, thus t8*cmesh*trees*finish*part must have been called.

### Prototype

```c
void t8_cmesh_trees_copy_part (t8_cmesh_trees_t trees_dest, int part_dest, t8_cmesh_trees_t trees_src, int part_src);
```
