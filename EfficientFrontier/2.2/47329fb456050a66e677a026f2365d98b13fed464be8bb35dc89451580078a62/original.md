```
    sCL(P::Problem)         define an empty Vector of struct sCL for Problem P

    struct sCL{T<:AbstractFloat}
```

Critical Line segment, with fields: default T = Float64

```
        S::Vector{Status}       # (N+J)x1
        K::Int              #number of IN assets
        L1::T                   #higher lambda
        I1::Vector{Event{T}}    #go in/out events at L1
        L0::T                   #lower lambda
        I0::Vector{Event{T}}    #go in/out events at L0
        alpha::Vector{T}        # K x 1
        beta::Vector{T}         # K x 1
```
