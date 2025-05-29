```
t8_stash_class_bsearch(stash, tree_id)
```

Search for an entry with a given tree index in the class-stash. The stash must be sorted beforehand.

# Arguments

  * `stash`:[in] The stash to be searched for.
  * `tree_id`:[in] The global tree id.

# Returns

The index of an element in the classes array of *stash* corresponding to *tree_id*. -1 if not found.

### Prototype

```c
ssize_t t8_stash_class_bsearch (t8_stash_t stash, t8_gloidx_t tree_id);
```
