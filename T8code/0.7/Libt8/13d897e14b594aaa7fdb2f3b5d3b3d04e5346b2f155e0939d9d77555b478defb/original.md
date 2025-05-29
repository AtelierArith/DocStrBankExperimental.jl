```
t8_cmesh_set_attribute(cmesh, gtree_id, package_id, key, data, data_size, data_persists)
```

Store an attribute at a tree in a cmesh. Attributes can be arbitrary data that is copied to an internal storage associated to the tree. Each application can set multiple attributes and attributes are distinguished by an integer key, where each application can use any integer as key.

!!! note
    If an attribute with the given package_id and key already exists, then it will get overwritten.


# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `gtree_id`:[in] The global id of the tree.
  * `package_id`:[in] Unique identifier of a valid software package.
  * `key`:[in] An integer key used to identify this attribute under all attributes with the same package_id. *key* must be a unique value for this tree and package_id.
  * `data`:[in] A pointer to the attribute data.
  * `data_size`:[in] The number of bytes of the attribute.
  * `data_persists`:[in] This flag can be used to optimize memory. If true then t8code assumes that the attribute data is present at the memory that *data* points to when t8*cmesh*commit is called (This is more memory efficient). If the flag is false an internal copy of the data is created immediately and this copy is used at commit. In both cases a copy of the data is used by t8_code after [`t8_cmesh_commit`](@ref).

# See also

[`sc_package_register`](@ref)

### Prototype

```c
void t8_cmesh_set_attribute (t8_cmesh_t cmesh, t8_gloidx_t gtree_id, int package_id, int key, void *data, size_t data_size, int data_persists);
```
