```
weight(d::ParticleSampleable, sample)
```

Return the weight of the given sample according to the given distribution.

This function automatically performs input validation and post-processing using the respective interface functions. The order of calls is

  * [`_assert_valid_input_type`](@ref)
  * [`_assert_valid_input`](@ref)
  * [`_weight`](@ref)
  * [`_post_processing`](@ref)
