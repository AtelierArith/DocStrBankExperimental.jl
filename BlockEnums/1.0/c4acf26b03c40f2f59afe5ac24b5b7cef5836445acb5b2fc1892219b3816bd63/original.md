```
numblocks(t::Type{<:BlockEnum{T}}) where T <: Integer
```

Return the number of blocks for which bookkeeping has been set up. The set of values of `t` is the nonzero values of `T`, which is typically very large. Bookkeeping of blocks requires storage. So you can only set up some of the blocks for use.
