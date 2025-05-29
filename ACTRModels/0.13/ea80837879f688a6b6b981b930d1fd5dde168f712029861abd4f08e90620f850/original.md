```
blend_chunks(actr, blended_slots, cur_time; request...)
```

Computes blended value over chunks given a retrieval request. Values are blended over the slots specified in `blended_slots`. Currently, blended is only supported  for numeric slot-values. 

# Arguments

  * `actr`: an `ACTR` model object
  * `blended_slots`: a set of slots over which slot-values are blended
  * `cur_time`: current simulated time

# Keywords

  * `request...`: optional keywords for the retrieval request
