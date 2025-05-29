```
ScaledWeightedCov(wtsm::AbstractMatrix{T})
```

!!! warning
    Experimental


Scaled weighted covariance matrix, where `wtsm` - `NxN` within block correlation matrix (N - total number of observations).  Used only for repeated effect. 

SWC = ScaledWeightedCov

$$
R = Corr(W) * \sigma_c^2
$$

where $Corr(W)$ - diagonal correlation matrix. 

example:

```julia
matwts = Symmetric(UnitUpperTriangular(rand(size(df0,1), size(df0,1))))
lmm = LMM(@formula(var~sequence+period+formulation), df0;
    repeated = VarEffect(@covstr(1|subject), SWC(matwts)))
fit!(lmm)

```

!!! note



There is no `wtsm` checks for symmetricity or values.
