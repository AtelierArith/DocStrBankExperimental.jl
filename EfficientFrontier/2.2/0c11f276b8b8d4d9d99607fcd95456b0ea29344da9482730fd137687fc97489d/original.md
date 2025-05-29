```
    computeCL!(aCL::Vector{sCL{T}}, S::Vector{Status}, PS::Problem{T}, nS::Settings{T}) where T
```

compute the Critical Line Segment for S::Vector{Status}, save to aCL[end]. Return value: true if done.
