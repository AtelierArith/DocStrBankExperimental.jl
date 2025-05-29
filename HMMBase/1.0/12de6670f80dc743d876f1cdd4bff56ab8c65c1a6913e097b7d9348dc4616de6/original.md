```
AbstractHMM{F<:VariateForm}
```

A custom HMM type must at-least implement the following interface:

```julia
struct CustomHMM{F,T} <: AbstractHMM{F}
    a::AbstractVector{T}               # Initial state distribution
    A::AbstractMatrix{T}               # Transition matrix
    B::AbstractVector{Distribution{F}} # Observations distributions
    # Optional, custom, fields ....
end
```
