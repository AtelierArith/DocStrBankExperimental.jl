```
t8_stash_attribute_is_owned(stash, index)
```

Return true if an attribute in the stash is owned by the stash, that is, it was copied in the call to [`t8_stash_add_attribute`](@ref). Returns false if the attribute is not owned by the stash.

# Arguments

  * `stash`:[in] The stash to be considered.
  * `index`:[in] The index of the attribute in the attribute array of *stash*.

# Returns

True of false.

### Prototype

```c
int t8_stash_attribute_is_owned (t8_stash_t stash, size_t index);
```
