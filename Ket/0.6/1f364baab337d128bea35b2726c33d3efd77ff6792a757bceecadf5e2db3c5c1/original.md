```
pretty_good_measurement(ρ::Vector{<:AbstractMatrix}, q::Vector{<:Real} = ones(length(ρ)))
```

Computes the pretty good measurement POVM for discriminating a vector of states `ρ` with probabilities `q`. If `q` is omitted it is assumed uniform.

Reference: Watrous, [Theory of Quantum Information Cp. 3](https://cs.uwaterloo.ca/~watrous/TQI/TQI.3.pdf)
