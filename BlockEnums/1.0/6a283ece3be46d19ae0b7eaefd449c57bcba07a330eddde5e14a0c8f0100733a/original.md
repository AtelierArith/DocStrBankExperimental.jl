```
maxvalind(t::Type{<:BlockEnum}, block_num::Integer)
```

Return the largest index for which a name has been assigned in the `block_num`th block `t`. This number is constrained to be within the values in the block.
