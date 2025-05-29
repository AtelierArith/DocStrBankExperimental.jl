```
compute_activation!(actr::AbstractACTR; request...)
```

Computes the activation of all chunks in declarative memory. By default, current time is computed with `get_time`.

# Arguments

  * `actr::AbstractACTR`: an `ACTR` object

# Keywords

  * `request...`: optional keywords for the retrieval request
