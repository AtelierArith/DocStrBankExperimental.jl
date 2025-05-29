LPV Spectral estimation result type.

See `ls_spectral_lpv` for additional help.

An object of this type can be plotted if `Plots.jl` is installed. Use regular Plots-syntax, with the additional attributes

```
normalization= :none / :sum / :max
normdim = :freq / :v # Only applies if normalization= :sum or :max
dims = 2 or 3 (default = 2)
```

Fields:

```
Y::AbstractVector
X::AbstractVector
V::AbstractVector
w
Nv
λ
coulomb::Bool
normalize::Bool
x                   # The estimated parameters
Σ                   # Covariance of the estimated parameters
```
