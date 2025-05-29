```
p4est_connectivity_permute(conn, perm, is_current_to_new)
```

[`p4est_connectivity_permute`](@ref) Given a permutation *perm* of the trees in a connectivity *conn*, permute the trees of *conn* in place and update *conn* to match.

### Parameters

  * `conn`:[in,out] The connectivity whose trees are permuted.
  * `perm`:[in] A permutation array, whose elements are size_t's.
  * `is_current_to_new`:[in] if true, the jth entry of perm is the new index for the entry whose current index is j, otherwise the jth entry of perm is the current index of the tree whose index will be j after the permutation.

### Prototype

```c
void p4est_connectivity_permute (p4est_connectivity_t * conn, sc_array_t * perm, int is_current_to_new);
```
