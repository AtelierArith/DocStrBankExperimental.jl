```
NeverTreatedParallel{C,S} <: TrendParallel{C,S}
```

Assume a parallel trends assumption holds between any group that received the treatment during the sample periods and a group that did not receive any treatment in any sample period. See also [`nevertreated`](@ref).

# Fields

  * `e::Tuple{Vararg{ValidTimeType}}`: group indices for units that did not receive any treatment.
  * `c::C`: an instance of [`ParallelCondition`](@ref).
  * `s::S`: an instance of [`ParallelStrength`](@ref).
