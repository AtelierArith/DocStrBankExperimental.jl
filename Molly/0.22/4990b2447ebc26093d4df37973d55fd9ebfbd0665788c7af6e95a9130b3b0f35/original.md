```
AverageObservableLogger(observable::Function, T::DataType, n_steps::Integer;
                        n_blocks::Integer=1024)
```

A logger that periodically records observations of a system and keeps a running empirical average.

While [`GeneralObservableLogger`](@ref) holds a full record of observations, [`AverageObservableLogger`](@ref) does not. In addition, calling `values(logger::AverageObservableLogger; std::Bool=true)` returns two values: the current running average, and an estimate of the standard deviation for this average based on the block averaging method described in [Flyvbjerg and Petersen 1989](https://doi.org/10.1063/1.457480).

# Arguments

  * `observable::Function`: the observable whose mean is recorded, must support   the method `observable(s::System, neighbors; n_threads::Integer)`.
  * `T::DataType`: the type returned by `observable`.
  * `n_steps::Integer`: number of simulation steps between observations.
  * `n_blocks::Integer=1024`: the number of blocks used in the block averaging   method, should be an even number.
