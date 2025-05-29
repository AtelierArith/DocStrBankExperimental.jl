```
qkf_smoother( Z, P, Z_pred, P_pred, T_bar, H_aug, G_aug, Φ_aug, dof ) -> (Z_smooth, P_smooth)
```

Out-of-place version of the QKF smoother. Returns new arrays rather than overwriting the input ones.

# Description

Identical to qkf*smoother! in logic, but it allocates new arrays Z*smooth and P_smooth for the smoothed results. This is often simpler for AD frameworks that do not allow in-place mutation of arrays.

# Returns

  * `Z_smooth::Matrix{T}`: (P × (T_bar+1)) smoothed states
  * `P_smooth::Array{T,3}`: (P × P × (T_bar+1)) smoothed covariances

# Example

```julia
Z_smooth, P_smooth = qkf_smoother(Z, P, Z_pred, P_pred, T_bar, Hn, Gn, H_aug, Φ_aug, n)
```
