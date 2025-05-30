```
setblocklength!(t::Type{<:BlockEnum}, block_length)
```

Set the length of each block in the partition of the values of `t`. This can only be called once.  In order to use the blocks you must first set up bookkeeping by calling `addblocks!`.  These blocks are called "active".
