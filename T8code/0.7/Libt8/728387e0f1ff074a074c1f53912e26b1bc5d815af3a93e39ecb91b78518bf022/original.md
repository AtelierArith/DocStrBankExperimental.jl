```
t8_cmesh_get_attribute_gloidx_array(cmesh, package_id, key, ltree_id, data_count)
```

Return the attribute pointer of a tree for a gloidx_t array.

!!! note
    *cmesh* must be committed before calling this function.


!!! note
    No check is performed whether the attribute actually stored *data_count* many entries since we do not store the number of data entries of the attribute array. You can keep track of the data count yourself by using another attribute.


# Arguments

  * `cmesh`:[in] The cmesh.
  * `package_id`:[in] The identifier of a valid software package.
  * `key`:[in] A key used to identify the attribute under all attributes of this tree with the same *package_id*.
  * `ltree_id`:[in] The local number of the tree.
  * `data_count`:[in] The number of entries in the array that are requested.  This must be smaller or equal to the *data_count* parameter of the corresponding call to t8*cmesh*set*attribute*gloidx_array

# Returns

The attribute pointer of the tree *ltree_id* or NULL if the attribute is not found.

# See also

[`sc_package_register`](@ref), [`t8_cmesh_set_attribute_gloidx_array`](@ref)

### Prototype

```c
t8_gloidx_t * t8_cmesh_get_attribute_gloidx_array (const t8_cmesh_t cmesh, const int package_id, const int key, const t8_locidx_t ltree_id, const size_t data_count);
```
