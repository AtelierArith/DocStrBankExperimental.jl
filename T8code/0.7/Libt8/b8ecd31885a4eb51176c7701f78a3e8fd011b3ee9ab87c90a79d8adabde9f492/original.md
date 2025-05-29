```
t8_stash_get_attribute(stash, index)
```

Return the pointer to an attribute in the stash.

# Arguments

  * `stash`:[in] The stash to be considered.
  * `index`:[in] The index of the attribute in the attribute array of *stash*.

# Returns

A void pointer to the memory region where the attribute is stored.

### Prototype

```c
void * t8_stash_get_attribute (t8_stash_t stash, size_t index);
```
