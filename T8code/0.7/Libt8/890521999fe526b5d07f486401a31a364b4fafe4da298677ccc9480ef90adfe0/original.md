```
t8_cmesh_set_attribute_string(cmesh, gtree_id, package_id, key, string)
```

Store a string as an attribute at a tree in a cmesh.

!!! note
    You can also use t8*cmesh*set_attribute, but we recommend using this specialized function for strings.


!!! note
    If an attribute with the given package_id and key already exists, then it will get overwritten.


# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `gtree_id`:[in] The global id of the tree.
  * `package_id`:[in] Unique identifier of a valid software package.
  * `key`:[in] An integer key used to identify this attribute under all attributes with the same package_id. *key* must be a unique value for this tree and package_id.
  * `string`:[in] The string to store as attribute.

# See also

[`sc_package_register`](@ref)

### Prototype

```c
void t8_cmesh_set_attribute_string (t8_cmesh_t cmesh, t8_gloidx_t gtree_id, int package_id, int key, const char *string);
```
