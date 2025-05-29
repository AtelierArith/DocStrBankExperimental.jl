```
p4est_lnodes_share_owned_begin(node_data, lnodes)
```

[`p4est_lnodes_share_owned_begin`](@ref)

*node_data* is a user-defined array of arbitrary type, where each entry is associated with the *lnodes* local nodes entry of matching index. For every local nodes entry that is owned by a process other than the current one, the value in the *node_data* array of the owning process is written directly into the *node_data* array of the current process. Values of *node_data* are not guaranteed to be sent or received until the *buffer* created by [`p4est_lnodes_share_owned_begin`](@ref) is passed to [`p4est_lnodes_share_owned_end`](@ref).

To be memory neutral, the *buffer* created by [`p4est_lnodes_share_owned_begin`](@ref) must be destroying with [`p4est_lnodes_buffer_destroy`](@ref) (it is not destroyed by [`p4est_lnodes_share_owned_end`](@ref)).

### Prototype

```c
p4est_lnodes_buffer_t *p4est_lnodes_share_owned_begin (sc_array_t * node_data, p4est_lnodes_t * lnodes);
```
