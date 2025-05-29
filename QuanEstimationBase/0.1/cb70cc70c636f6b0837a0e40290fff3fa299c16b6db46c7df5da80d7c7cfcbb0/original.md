```
CFIM(ρ::Matrix{T}, dρ::Vector{Matrix{T}}; M=nothing, eps=GLOBAL_EPS) where {T<:Complex}
```

When the set of POVM is not given. Calculate the CFIM with SIC-POVM. The SIC-POVM is generated from the Weyl-Heisenberg covariant SIC-POVM fiducial state which can be downloaded from [here](http://www.physics.umb.edu/Research/QBism/solutions.html).
