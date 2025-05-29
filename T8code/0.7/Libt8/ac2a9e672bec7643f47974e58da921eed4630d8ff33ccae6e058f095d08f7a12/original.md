```
t8_cmesh_set_partition_range(cmesh, set_face_knowledge, first_local_tree, last_local_tree)
```

Declare if the cmesh is understood as a partitioned cmesh and specify the processor local tree range. This function should be preferred over t8*cmesh*set*partition*offsets when the cmesh is not derived from another cmesh. This call is only valid when the cmesh is not yet committed via a call to t8*cmesh*commit.

!!! note
    A value of *set*face*knowledge* other than -1 or 3 is not yet supported.


# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `set_face_knowledge`:[in] Several values are possible that define how much information is required on face connections, specified by t8*cmesh*set*join. 0: Expect face connection of local trees. 1: In addition, expect face connection from ghost trees to local trees. 2: In addition, expect face connection between ghost trees. 3: Expect face connection of local and ghost trees. Consistency of this requirement is checked on t8*cmesh*commit. -1: Do not change the face\*knowledge level but keep any previously set ones. (Possibly by a previous call to t8*cmesh*set*partition*range)
  * `first_local_tree`:[in] The global index ID of the first tree on this process. If this tree is also the last tree on the previous process, then the argument must be -ID - 1.
  * `last_local_tree`:[in] The global index of the last tree on this process. If this process should be empty then *last*local*tree* must be strictly smaller than *first*local*tree*.

# See also

t8_cmesh_set_partition_offset, [`t8_cmesh_set_partition_uniform`](@ref)

### Prototype

```c
void t8_cmesh_set_partition_range (t8_cmesh_t cmesh, int set_face_knowledge, t8_gloidx_t first_local_tree, t8_gloidx_t last_local_tree);
```
