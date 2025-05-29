```
T0 = get_block_start_times(seq::Sequence)
```

Returns a vector containing the start times of blocks in a sequence. The initial time is always zero, and the final time corresponds to the duration of the sequence.

# Arguments

  * `seq`: (`::Sequence`) Sequence struct

# Returns

  * `T0`: (`::Vector`, `[s]`) start times of the blocks in a sequence
