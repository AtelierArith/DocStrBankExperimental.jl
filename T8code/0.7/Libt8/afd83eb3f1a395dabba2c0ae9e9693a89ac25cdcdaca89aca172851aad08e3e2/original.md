```
t8_cmesh_get_attribute(cmesh, package_id, key, ltree_id)
```

Return the attribute pointer of a tree.

!!! note
    *cmesh* must be committed before calling this function.


# Arguments

  * `cmesh`:[in] The cmesh.
  * `package_id`:[in] The identifier of a valid software package.
  * `key`:[in] A key used to identify the attribute under all attributes of this tree with the same *package_id*.
  * `tree_id`:[in] The local number of the tree.

# Returns

The attribute pointer of the tree *ltree_id* or NULL if the attribute is not found.

# See also

[`sc_package_register`](@ref), [`t8_cmesh_set_attribute`](@ref)

### Prototype

```c
void * t8_cmesh_get_attribute (const t8_cmesh_t cmesh, const int package_id, const int key, const t8_locidx_t ltree_id);
```
