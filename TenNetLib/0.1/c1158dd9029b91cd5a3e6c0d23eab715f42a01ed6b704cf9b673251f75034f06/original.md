```
function CouplingModel(os::OpStrings{T1},
                       mpo::MPO;
                       merge::Bool = true,
                       maxdim::Int = typemax(Int),
                       mindim::Int = 1,
                       cutoff::Float64 = Float64_threshold(),
                       svd_alg::String = "divide_and_conquer",
                       chunksize::Int = 12) where {T1 <: Number}
```

Constructor of the `CouplingModel` from `os::OpStrings` and `mpo::MPO`. Resultant `CouplingModel` is the sum of `os` and the `mpo`.

#### Named arguments and their default values:

  * `merge::Bool = true`. If `true`, merges all the terms having same spatial support resulting in larger virtual dimension. Otherwise, all the terms have virtual dimension one.
  * `maxdim::Int = typemax(Int)`: Maximum bond dimension after SVD truncation.
  * `mindim::Int = 1`: Minimum bond dimension after SVD truncation.
  * `cutoff::Float64 = Float64_Threshold()`: Cutoff for SVD truncation.
  * `svd_alg::String = "divide_and_conquer"`.
  * `chunksize::Int = 12`.
