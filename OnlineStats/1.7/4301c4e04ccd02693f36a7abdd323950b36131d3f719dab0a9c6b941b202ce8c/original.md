```
ProbMap(T::Type; weight=EqualWeight())
ProbMap(A::AbstractDict{T, Float64}; weight=EqualWeight())
```

Track a dictionary that maps unique values to its probability.  Similar to [`CountMap`](@ref), but uses a weighting mechanism.

# Example

```
o = ProbMap(Int)
fit!(o, rand(1:10, 1000))
probs(o)
```
