```
add_chunk!(memory::Declarative, cur_time=0.0; act=0.0, slots...)
```

Adds new chunk to declarative memory or updates existing chunk with new use

# Arguments

  * `memory::Declarative`: declarative memory object
  * `cur_time=0.0`: current simulated time in seconds
  * `bl=0.0`: baselevel constant for new/updated chunk

# Keywords

  * `slots...`: optional keyword arguments corresponding to slot-value pairs, e.g. name=:Bob
