```
union_ghost(indices,gids,owners)
```

Make the union of the ghost indices in `indices` with   the global indices `gids` and owners `owners`.  Return an object  of the same type as `indices` with the new ghost indices and the same  own indices as in `indices`.  The result does not take ownership of `gids`  and `owners`. 
