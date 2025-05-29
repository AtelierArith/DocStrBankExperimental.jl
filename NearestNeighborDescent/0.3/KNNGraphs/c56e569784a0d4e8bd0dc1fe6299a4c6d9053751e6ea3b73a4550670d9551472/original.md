```
update_flag!(graph, v, i, new_flag)
```

Update the flag of node `v`s ith outgoing edge. Returns the new edge. Note that since the flags don't influence the edge ordering, this can't invalidate the heap invariant.
