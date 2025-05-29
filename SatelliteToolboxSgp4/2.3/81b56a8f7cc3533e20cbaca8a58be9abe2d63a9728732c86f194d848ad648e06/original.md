```
fit_sgp4_tle(vjd::AbstractVector{Tjd}, vr_teme::AbstractVector{Tv}, vv_teme::AbstractVector{Tv}; kwargs...) where {T<:Number, Tepoch<:Number, Tjd<:Number, Tv<:AbstractVector} -> TLE, SMatrix{7, 7, T}
```

Fit a Two-Line Element set (`TLE`) for the SGP4 orbit propagator using the osculating elements represented by a set of position vectors `vr_teme` [km] and a set of velocity vectors `vv_teme` [km / s] represented in the True-Equator, Mean-Equinox reference frame (TEME) at instants in the array `vjd` [Julian Day].

This algorithm was based on **[1]**.

!!! note
    This algorithm version will allocate a new SGP4 propagator with the default constants `sgp4c_wgs84`. If another set of constants are required, use the function [`fit_sgp4_tle!`](@ref) instead.


# Keywords

  * `atol::Number`: Tolerance for the residue absolute value. If the residue is lower than   `atol` at any iteration, the computation loop stops.   (**Default** = 2e-4)
  * `rtol::Number`: Tolerance for the relative difference between the residues. If the   relative difference between the residues in two consecutive iterations is lower than   `rtol`, the computation loop stops.   (**Default** = 2e-4)
  * `estimate_bstar::Bool`: If `true`, the algorithm will try to estimate the B* parameter.   Otherwise, it will be set to 0 or to the value in initial guess (see section  **Initial   Guess**).   (**Default** = true)
  * `initial_guess::Union{Nothing, AbstractVector, TLE}`: Initial guess for the TLE fitting   process. If it is `nothing`, the algorithm will obtain an initial estimate from the   osculating elements in `vr_teme` and `vv_teme`. For more information, see the section   **Initial Guess**.   (**Default** = nothing)
  * `jacobian_perturbation::Number`: Initial state perturbation to compute the   finite-difference when calculating the Jacobian matrix.   (**Default** = 1e-3)
  * `jacobian_perturbation_tol::Number`: Tolerance to accept the perturbation when calculating   the Jacobian matrix. If the computed perturbation is lower than   `jacobian_perturbation_tol`, we increase it until it absolute value is higher than   `jacobian_perturbation_tol`.   (**Default** = 1e-7)
  * `max_iterations::Int`: Maximum number of iterations allowed for the least-square fitting.   (**Default** = 50)
  * `mean_elements_epoch::Number`: Epoch for the fitted TLE.   (**Default** = vjd[end])
  * `verbose::Bool`: If `true`, the algorithm prints debugging information to `stdout`.   (**Default** = true)
  * `weight_vector::AbstractVector`: Vector with the measurements weights for the least-square   algorithm. We assemble the weight matrix `W` as a diagonal matrix with the elements in   `weight_vector` at its diagonal.   (**Default** = `@SVector(ones(Bool, 6))`)
  * `classification::Char`: Satellite classification character for the output TLE.   (**Default** = 'U')
  * `element_set_number::Int`: Element set number for the output TLE.   (**Default** = 0)
  * `international_designator::String`: International designator string for the output TLE.   (**Default** = "999999")
  * `name::String`: Satellite name for the output TLE.   (**Default** = "UNDEFINED")
  * `revolution_number::Int`: Revolution number for the output TLE.   (**Default** = 0)
  * `satellite_number::Int`: Satellite number for the output TLE.   (**Default** = 9999)

# Returns

  * `TLE`: The fitted TLE.
  * `SMatrix{7, 7, T}`: Final covariance matrix of the least-square algorithm.

# Initial Guess

This algorithm uses a least-square algorithm to fit a TLE based on a set of osculating state vectors. Since the system is chaotic, a good initial guess is paramount for algorithm convergence. We can provide an initial guess using the keyword `initial_guess`.

If `initial_guess` is a `TLE`, we update the TLE epoch using the function [`update_sgp4_tle_epoch!`](@ref) to the desired one in `mean_elements_epoch`. Afterward, we use this new TLE as the initial guess.

If `initial_guess` is an `AbstractVector`, we use this vector as the initial mean state vector for the algorithm. It must contain 7 elements as follows:

```
┌                                    ┐
│ IDs 1 to 3: Mean position [km]     │
│ IDs 4 to 6: Mean velocity [km / s] │
│ ID  7:      Bstar         [1 / er] │
└                                    ┘
```

If `initial_guess` is `nothing`, the algorithm takes the closest osculating state vector to the `mean_elements_epoch` and uses it as the initial mean state vector. In this case, the epoch is set to the same epoch of the osculating data in `vjd`. When the fitted TLE is obtained, the algorithm uses the function [`update_sgp4_tle_epoch!`](@ref) to change its epoch to `mean_elements_epoch`.

!!! note
    If `initial_guess` is not `nothing`, the B* initial estimate is obtained from the TLE or the state vector. Hence, if `estimate_bstar` is `false`, it will be kept constant with this initial value.


# Examples

```julia-repl
julia> vr_teme = [
           [-6792.402703741442, 2192.6458461287293, 0.18851758695295118],
           [-6357.88873265975, 2391.9476768911686, 2181.838771262736]
       ];

julia> vv_teme = [
           [0.3445760107690598, 1.0395135806993514, 7.393686131436984],
           [2.5285015912807003, 0.27812476784300005, 7.030323100703928]
       ];

julia> vjd = [
           2.46002818657856e6,
           2.460028190050782e6
       ];

julia> tle, P = fit_sgp4_tle(vjd, vr_teme, vv_teme; estimate_bstar = false)
ACTION:   Fitting the TLE.
           Iteration        Position RMSE        Velocity RMSE           Total RMSE       RMSE Variation
                                     [km]             [km / s]                  [ ]
PROGRESS:          3          5.80079e-09          4.38304e-07          4.38343e-07             -99.9514 %

(TLE: UNDEFINED (Epoch = 2023-03-24T16:33:40.388), [1.085542785763592 -0.02468955108588304 … -0.07505082051267041 -5691.217934788844; -0.024689551096344593 1.0180284581267773 … 0.023015858293558573 1745.6307022638805; … ; -0.07505082051315085 0.023015858293655808 … 0.06515845129137222 4946.150014964575; -5691.217934826224 1745.630702271188 … 4946.15001496459 3.7558624425042915e8])

julia> tle
TLE:
                      Name : UNDEFINED
          Satellite number : 9999
  International designator : 999999
        Epoch (Year / Day) : 23 /  83.69005079 (2023-03-24T16:33:40.388)
        Element set number : 0
              Eccentricity :   0.00012463
               Inclination :  98.43040000 deg
                      RAAN : 162.11312239 deg
       Argument of perigee : 136.15040637 deg
              Mean anomaly : 241.97934028 deg
           Mean motion (n) :  14.40814157 revs / day
         Revolution number : 0
                        B* :            0 1 / er
                     ṅ / 2 :            0 rev / day²
                     n̈ / 6 :            0 rev / day³
```

# References

  * **[1]** Vallado, D. A., Crawford, P (2008). SGP4 Orbit Determination. American Institute   of Aeronautics ans Astronautics.
