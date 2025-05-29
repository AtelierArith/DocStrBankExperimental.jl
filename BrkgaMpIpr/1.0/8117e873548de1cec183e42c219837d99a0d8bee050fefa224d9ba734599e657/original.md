```
affect_solution_kendall_tau(block1::SubArray{Float64, 1},
                            block2::SubArray{Float64, 1})::Bool
```

Return `true` the the changing of the blocks of keys `block1` by the blocks of keys `block2` affects the solution, based on the [Kendall Tau distance.](https://en.wikipedia.org/wiki/Kendall_tau_distance)

!!! note
    `block1` and `block2` must have the same size. No bounds checking is done due to performance reasons.


# Arguments

  * `block1::SubArray{Float64, 1}`: the first vector.
  * `block2::SubArray{Float64, 1}`: the second vector.
