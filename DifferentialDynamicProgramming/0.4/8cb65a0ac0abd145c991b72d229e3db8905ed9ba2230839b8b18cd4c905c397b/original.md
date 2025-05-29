```
`GaussianPolicy{P}`
```

# Fileds:

```
T::Int          # number of time steps
n::Int          # State dimension
m::Int          # Number of control inputs
K::Array{P,3}   # Time-varying feedback gain ∈ R(n,m,T)
k::Array{P,2}   # Open loop control signal  ∈ R(m,T)
Σ::Array{P,3}   # Time-varying controller covariance  ∈ R(m,m,T)
Σi::Array{P,3}  # The inverses of Σ
```
