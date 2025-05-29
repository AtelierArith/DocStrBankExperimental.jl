```
t8_cmesh_set_attribute_gloidx_array(cmesh, gtree_id, package_id, key, data, data_count, data_persists)
```

Store an array of [`t8_gloidx_t`](@ref) as an attribute at a tree in a cmesh.

!!! note
    You can also use t8*cmesh*set_attribute, but we recommend using this specialized function for arrays.


!!! note
    If an attribute with the given package_id and key already exists, then it will get overwritten.


!!! note
    We do not store the number of data entries *data_count* of the attribute array. You can keep track of the data count yourself by using another attribute.


# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `gtree_id`:[in] The global id of the tree.
  * `package_id`:[in] Unique identifier of a valid software package.
  * `key`:[in] An integer key used to identify this attribute under all attributes with the same package_id. *key* must be a unique value for this tree and package_id.
  * `data`:[in] The array to store as attribute.
  * `data_count`:[in] The number of entries in *data*.
  * `data_persists`:[in] This flag can be used to optimize memory. If true then t8code assumes that the attribute data is present at the memory that *data* points to when t8*cmesh*commit is called (This is more memory efficient). If the flag is false an internal copy of the data is created immediately and this copy is used at commit. In both cases a copy of the data is used by t8_code after [`t8_cmesh_commit`](@ref).

# See also

[`sc_package_register`](@ref)

### Prototype

```c
void t8_cmesh_set_attribute_gloidx_array (t8_cmesh_t cmesh, t8_gloidx_t gtree_id, int package_id, int key, const t8_gloidx_t *data, const size_t data_count, int data_persists);
```
