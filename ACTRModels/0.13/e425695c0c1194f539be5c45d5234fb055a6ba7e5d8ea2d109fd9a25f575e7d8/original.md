```
get_chunks(actr::AbstractACTR, funs...; check_value=true, criteria...)
```

Returns all chunks that matches a set criteria using `funs...` as matching functions.

# Arguments

  * `actr::AbstractACTR`: an ACT-R model object
  * `funs...`: a list of functions

# Keywords

  * `check_value=true`: check slot value
  * `criteria...`: optional keyword arguments corresponding to critiria for matching chunk
