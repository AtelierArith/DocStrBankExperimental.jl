```
t8_cmesh_set_tree_class(cmesh, gtree_id, tree_class)
```

Set the class of a tree in the cmesh. It is not allowed to call this function after t8*cmesh*commit. It is not allowed to call this function multiple times for the same tree.

# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `tree_id`:[in] The global number of the tree.
  * `tree_class`:[in] The element class of this tree.

### Prototype

```c
void t8_cmesh_set_tree_class (t8_cmesh_t cmesh, t8_gloidx_t gtree_id, t8_eclass_t tree_class);
```
