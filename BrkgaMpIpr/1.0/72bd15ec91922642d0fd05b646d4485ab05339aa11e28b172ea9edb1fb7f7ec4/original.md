```
affect_solution_hamming_distance(block1::SubArray{Float64, 1},
                                 block2::SubArray{Float64, 1},
                                 threshold::Float64 = 0.5)::Bool
```

Return `true` the the changing of the blocks of keys `block1` by the blocks of keys `block2` affects the solution, based on the [Hamming distance](https://en.wikipedia.org/wiki/Hamming_distance).

!!! note
    This function may be more appropriated to threshold/direct chromosome representations.


!!! note
    `block1` and `block2` must have the same size. No bounds checking is done due to performance reasons.


!!! note
    This function is annotated with `@inline` due to performance reasons too.


# Arguments

  * `block1::SubArray{Float64, 1}`: the first vector.
  * `block2::SubArray{Float64, 1}`: the second vector.
  * `threshold::Float64 = 0.5`: the threshold for binarization.
