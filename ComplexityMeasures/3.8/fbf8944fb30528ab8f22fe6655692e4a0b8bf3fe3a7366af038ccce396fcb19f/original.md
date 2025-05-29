```
Probabilities <: Array{<:AbstractFloat, N}
Probabilities(probs::Array [, outcomes [, dimlabels]]) → p
Probabilities(counts::Counts [, outcomes [, dimlabels]]) → p
```

`Probabilities` stores an `N`-dimensional array of probabilities, while ensuring that the array sums to 1 (normalized probability mass). In most cases the array is a standard vector. `p` itself can be manipulated and iterated over, just like its stored array.

The probabilities correspond to `outcomes` that describe the axes of the array. If `p isa Probabilities`, then `p.outcomes[i]` is an an abstract vector containing the outcomes along the `i`-th dimension. The outcomes have the same ordering as the probabilities, so that `p[i][j]` is the probability for outcome `p.outcomes[i][j]`. The dimensions of the array are named, and can be accessed by `p.dimlabels`, where `p.dimlabels[i]` is the label of the `i`-th dimension. Both `outcomes` and `dimlabels` are assigned automatically if not given. If the input is a set of [`Counts`](@ref), and `outcomes` and `dimlabels` are not given, then the labels and outcomes are inherited from the counts.

## Examples

```julia
julia> probs = [0.2, 0.2, 0.2, 0.2]; Probabilities(probs) # will be normalized to sum to 1
 Probabilities{Float64,1} over 4 outcomes
 Outcome(1)  0.25
 Outcome(2)  0.25
 Outcome(3)  0.25
 Outcome(4)  0.25
```

```julia
julia> c = Counts([12, 16, 12], ["out1", "out2", "out3"]); Probabilities(c)
 Probabilities{Float64,1} over 3 outcomes
 "out1"  0.3
 "out2"  0.4
 "out3"  0.3
```
