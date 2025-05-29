```
t8_stash_add_attribute(stash, id, package_id, key, size, attr, copy)
```

Add an attribute to a tree.

# Arguments

  * `stash`:[in] The stash structure to be modified.
  * `id`:[in] The global index of the tree to which the attribute is added.
  * `package_id`:[in] The unique id of the current package.
  * `key`:[in] An integer value used to identify this attribute.
  * `size`:[in] The size (in bytes) of the attribute.
  * `attr`:[in] Points to *size* bytes of memory that should be stored as the attribute.
  * `copy`:[in] If true the attribute data is copied from *attr* to an internal storage. If false only the pointer *attr* is stored and the data is only copied if the cmesh is committed. (More memory efficient).

### Prototype

```c
void t8_stash_add_attribute (t8_stash_t stash, t8_gloidx_t id, int package_id, int key, size_t size, void *const attr, int copy);
```
