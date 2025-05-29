```
ornstein_zernike_v(dim::Int, ρ::Float64, g2::Function, s::Function, closure::String, r_vec::AbstractVector = 0.025:0.05:10,
k_vec::AbstractVector = 0.025:0.05:20) :: Interpolations.GriddedInterpolation
```

Compute the Ornstein-Zernike potential ($βv(r)$) using the Ornstein-Zernike equation.

## Arguments

  * `dim::Int`: The dimensionality of the system.
  * `ρ::Real`: The number density (particles per unit volume) of the system.
  * `g2::Function`: The pair correlation function $g_2(r)$ as a function of $r$.
  * `s::Function`: The structure factor $S(k)$ as a function of $k$.
  * `closure::String`: The closure relation to be used in the Ornstein-Zernike equation. Possible values are:

      * "PMF": Potential of mean force, basically $-\ln(g_2(r))$.
      * "MFA":Mean-Field Approximation (MFA).
      * "HNC": Hypernetted Chain closure.
      * "PY": Percus-Yevick closure.

## Optional Arguments

  * `r_vec::AbstractVector`: A vector of r values at which the g_2(r) function is valid. Default is 0.025:0.05:10.
  * `k_vec::AbstractVector`: A vector of k values at which the S(k) function is valid. Default is 0.025:0.05:20.

## Returns

  * An instance of `Interpolations.GriddedInterpolation` representing the OZ potential $βv(r)$, which can be used as a regular function.

Note: The `g2` and `s` functions should be provided as valid functions that return the pair correlation function and structure factor, respectively, as a function of r and k.

## Example:

```
function pair_correlation_function(r)
    # Define the pair correlation function here

    # ...
end
function structure_factor(k)
    # Define the structure factor here

    # ...
end
closure_type = "PY"
oz_v = ornstein_zernike_v(3, 0.5, pair_correlation_function, structure_factor, closure_type)
```
