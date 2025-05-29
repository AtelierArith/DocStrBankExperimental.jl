```
treated_ids(x <: BalancedPanel)

Returns the indices of treated units in the panel, so that Y[treated_ids(x), :] returns a
(Nₜᵣ×T) matrix of outcomes for treated units in all periods.
```
