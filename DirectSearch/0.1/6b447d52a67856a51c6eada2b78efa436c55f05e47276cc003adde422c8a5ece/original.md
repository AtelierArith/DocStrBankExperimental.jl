```
SetInitialPoint(p::DSProblem{T}, x::Vector{T}) where T
```

Set the initial incumbent point to `x`. This must be of the correct dimension. If using any extreme barrier constraints then it must also satisfy these constraints.
