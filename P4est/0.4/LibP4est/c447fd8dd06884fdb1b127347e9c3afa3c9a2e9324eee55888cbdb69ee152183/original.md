```
p8est_lnodes_share_all_begin(node_data, lnodes)
```

[`p8est_lnodes_share_all_begin`](@ref)

*node_data* is a user_defined array of arbitrary type, where each entry is associated with the *lnodes* local nodes entry of matching index. For every process that shares an entry with the current one, the value in the *node_data* array of that process is written into a *buffer*->recv*buffers entry as described above. The user can then perform some arbitrary work that requires the data from all processes that share a node (such as reduce, max, min, etc.). When the work concludes, the *buffer* should be destroyed with [`p8est*lnodes*buffer*destroy`](@ref).

Values of *node_data* are not guaranteed to be send, and *buffer*->recv*buffer entries are not guaranteed to be received until the *buffer* created by [`p8est*lnodes*share*all*begin`](@ref) is passed to [`p8est*lnodes*share*all_end`](@ref).

### Prototype

```c
p8est_lnodes_buffer_t *p8est_lnodes_share_all_begin (sc_array_t * node_data, p8est_lnodes_t * lnodes);
```
