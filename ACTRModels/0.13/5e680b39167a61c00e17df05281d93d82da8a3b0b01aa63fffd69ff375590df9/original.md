```
blend_chunks(actr::AbstractACTR, blended_slots; request...)
```

Computes blended value over chunks given a retrieval request. By default,  values are blended over the set of slots formed by the set difference between all  slots of a chunk and the slots specified in the retrieval request. The default time used  in activation calculations is taken from `get_time(actr`). Currently, blended  is only supported for numeric slot-values. 

# Arguments

  * `actr::AbstractACTR`: an `ACTR` model object
  * `blended_slots`: a set of slots over which slot-values are blended

# Keywords

  * `request...`: optional keywords for the retrieval request
