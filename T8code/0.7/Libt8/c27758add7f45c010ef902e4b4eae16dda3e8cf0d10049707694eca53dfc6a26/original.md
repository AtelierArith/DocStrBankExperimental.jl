```
t8_cmesh_trees_is_face_consistent(cmesh, trees)
```

Check whether the face connection of a trees structure are consistent. That is if tree1 lists tree2 as neighbor at face i with ttf entries (or,face j), then tree2 must list tree1 as neighbor at face j with ttf entries (or, face i).

# Arguments

  * `cmesh`:[in] A cmesh structure to be checked.
  * `trees`:[in] The cmesh's trees struct.

# Returns

True if the face connections are consistent, False if not.

### Prototype

```c
int t8_cmesh_trees_is_face_consistent (t8_cmesh_t cmesh, t8_cmesh_trees_t trees);
```
