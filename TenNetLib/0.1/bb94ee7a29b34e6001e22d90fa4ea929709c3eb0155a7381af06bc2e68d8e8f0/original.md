```
function CouplingModel(os::OpStrings{T1},
                       sites::Vector{Index{T2}};
                       merge::Bool = true,
                       maxdim::Int = typemax(Int),
                       mindim::Int = 1,
                       cutoff::Float64 = Float64_threashold(),
                       svd_alg::String = "divide_and_conquer",
                       chunksize::Int = 12) where {T1 <: Number, T2}
```

Constructor of the `CouplingModel` from `os::OpStrings` and `sites::Vector{Index}`.

#### Named arguments and their default values:

  * `merge::Bool = true`. If `true`, merges all the terms having same spatial support resulting in larger virtual dimension. Otherwise, all the terms have virtual dimension one.
  * `maxdim::Int = typemax(Int)`: Maximum bond dimension after SVD truncation.
  * `mindim::Int = 1`: Minimum bond dimension after SVD truncation.
  * `cutoff::Float64 = Float64_Threshold()`: Cutoff for SVD truncation.
  * `svd_alg::String = "divide_and_conquer"`.
  * `chunksize::Int = 12`.

#### Example:

```
os = OpStrings()    
for j=1:N-1
    os += 1, "Sz" => j, "Sz" => j+1
    os += 0.5, "S+" => j, "S-" => j+1
    os += 0.5, "S-" => j, "S+" => j+1
end    
H = CouplingModel(os,sites)
```
