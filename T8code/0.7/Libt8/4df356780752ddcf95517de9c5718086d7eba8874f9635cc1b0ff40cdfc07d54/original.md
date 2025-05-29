```
t8_cmesh_set_join(cmesh, gtree1, gtree2, face1, face2, orientation)
```

Insert a face-connection between two trees in a cmesh.

# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `tree1`:[in] The tree id of the first of the two trees.
  * `tree2`:[in] The tree id of the second of the two trees.
  * `face1`:[in] The face number of the first tree.
  * `face2`:[in] The face number of the second tree.
  * `orientation`:[in] Specify how face1 and face2 are oriented to each other TODO: orientation needs to be carefully defined for all element classes. TODO: document orientation

### Prototype

```c
void t8_cmesh_set_join (t8_cmesh_t cmesh, t8_gloidx_t gtree1, t8_gloidx_t gtree2, int face1, int face2, int orientation);
```
