```
GivenSequenceAM(X::Matrix{...})
GivenSequenceAM(X::Vector{Vector{...}})
```

A dummy acquisition maximizer that returns the predefined sequence of points in the given order. The maximizer throws an error if it runs out of points in the sequence.

# See Also

[`GivenPointAM`](@ref),
