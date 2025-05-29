```
t8_offset_sendsto(proca, procb, t8_offset_from, t8_offset_to)
```

Query whether in a repartitioning setting, a given process sends local trees (and then possibly ghosts) to a given other process.

# Arguments

  * `proca`:[in] Mpi rank of the possible sending process.
  * `procb`:[in] Mpi rank of the possible receiver.
  * `offset_from`:[in] The partition table of the current partition.
  * `offset_to`:[in] The partition table of the next partition.

# Returns

nonzero if *proca* does send local trees to *procb* when we repartition from *offset_from* to *offset_to*. 0 else.

### Prototype

```c
int t8_offset_sendsto (int proca, int procb, const t8_gloidx_t *t8_offset_from, const t8_gloidx_t *t8_offset_to);
```
