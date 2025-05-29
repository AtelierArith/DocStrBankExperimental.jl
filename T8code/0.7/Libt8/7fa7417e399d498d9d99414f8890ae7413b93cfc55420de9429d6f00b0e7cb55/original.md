```
t8_offset_sendstree(proc_send, proc_to, gtree, offset_from, offset_to)
```

Query whether in a repartitioning setting, a given process sends a given tree to a second process.

# Arguments

  * `proc_send`:[in] Mpi rank of the possible sending process.
  * `proc_recv`:[in] Mpi rank of the possible receiver.
  * `gtree`:[in] A global tree id.
  * `offset_from`:[in] The partition table of the current partition.
  * `offset_to`:[in] The partition table of the next partition.

# Returns

nonzero if *proc_send* will send the tree *gtree* to *proc_recv*. 0 else. When calling, *gtree* must not be a local tree of *proc_send* in *offset_from*. In this case, 0 is always returned.

### Prototype

```c
int t8_offset_sendstree (int proc_send, int proc_to, t8_gloidx_t gtree, const t8_gloidx_t *offset_from, const t8_gloidx_t *offset_to);
```
