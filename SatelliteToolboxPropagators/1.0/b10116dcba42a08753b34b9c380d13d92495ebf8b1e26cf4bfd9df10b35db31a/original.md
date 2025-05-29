```
fit_j4osc_mean_elements!(j4oscd::J4OsculatingPropagator{Tepoch, T}, vjd::AbstractVector{Tjd}, vr_i::AbstractVector{Tv}, vv_i::AbstractVector{Tv}; kwargs...) where {T<:Number, Tepoch<:Number, Tjd<:Number, Tv<:AbstractVector} -> KeplerianElements{Tepoch, T}, SMatrix{6, 6, T}
```

Fit a set of mean Keplerian elements for the J4 osculating orbit propagator `j4oscd` using the osculating elements represented by a set of position vectors `vr_i` [m] and a set of velocity vectors `vv_i` [m / s] represented in an inertial reference frame at instants in the array `vjd` [Julian Day].

!!! note
    The J4 osculating orbit propagator `j4oscd` will be initialized with the Keplerian elements returned by the function.


# Keywords

  * `atol::Number`: Tolerance for the residue absolute value. If the residue is lower than   `atol` at any iteration, the computation loop stops.   (**Default** = 2e-4)
  * `rtol::Number`: Tolerance for the relative difference between the residues. If the   relative difference between the residues in two consecutive iterations is lower than   `rtol`, the computation loop stops.   (**Default** = 2e-4)
  * `initial_guess::Union{Nothing, KeplerianElements}`: Initial guess for the mean elements   fitting process. If it is `nothing`, the algorithm will obtain an initial estimate from   the osculating elements in `vr_i` and `vv_i`.   (**Default** = nothing)
  * `jacobian_perturbation::Number`: Initial state perturbation to compute the   finite-difference when calculating the Jacobian matrix.   (**Default** = 1e-3)
  * `jacobian_perturbation_tol::Number`: Tolerance to accept the perturbation when calculating   the Jacobian matrix. If the computed perturbation is lower than   `jacobian_perturbation_tol`, we increase it until it absolute value is higher than   `jacobian_perturbation_tol`.   (**Default** = 1e-7)
  * `max_iterations::Int`: Maximum number of iterations allowed for the least-square fitting.   (**Default** = 50)
  * `mean_elements_epoch::Number`: Epoch for the fitted mean elements.   (**Default** = vjd[end])
  * `verbose::Bool`: If `true`, the algorithm prints debugging information to `stdout`.   (**Default** = true)
  * `weight_vector::AbstractVector`: Vector with the measurements weights for the least-square   algorithm. We assemble the weight matrix `W` as a diagonal matrix with the elements in   `weight_vector` at its diagonal.   (**Default** = `@SVector(ones(Bool, 6))`)

# Returns

  * `KeplerianElements{Tepoch, T}`: Fitted Keplerian elements.
  * `SMatrix{6, 6, T}`: Final covariance matrix of the least-square algorithm.

# Examples

```julia-repl
# Allocate a new J4 osculating orbit propagator using a dummy Keplerian elements.
julia> j4oscd = j4osc_init(KeplerianElements{Float64, Float64}(0, 7000e3, 0, 0, 0, 0, 0));

julia> vr_i = [
           [-6792.402703741442, 2192.6458461287293, 0.18851758695295118] .* 1000,
           [-6357.88873265975, 2391.9476768911686, 2181.838771262736] .* 1000
       ];

julia> vv_i = [
           [0.3445760107690598, 1.0395135806993514, 7.393686131436984] .* 1000,
           [2.5285015912807003, 0.27812476784300005, 7.030323100703928] .* 1000
       ];

julia> vjd = [
           2.46002818657856e6,
           2.460028190050782e6
       ];

julia> orb, P = fit_j4osc_mean_elements!(j4oscd, vjd, vr_i, vv_i)
ACTION:   Fitting the mean elements for the J4 osculating propagator.
           Iteration        Position RMSE        Velocity RMSE           Total RMSE       RMSE Variation
                                     [km]             [km / s]                  [ ]
PROGRESS:          4          1.68852e-05           0.00259716              2.59722          6.52143e-10 %

(KeplerianElements{Float64, Float64}: Epoch = 2.46003e6 (2023-03-24T16:33:40.388), [0.999942775712293 -0.004901178682591695 … -0.00012021347649120565 -0.0001155014732440418; -0.004901178674245216 1.0007325984965127 … 0.0032661543862499806 3.8581997167487534e-5; … ; -0.00012021347646254671 0.003266154386250846 … 2.204822797002821e-5 5.3982040158043245e-8; -0.00011550147323899825 3.8581997169916946e-5 … 5.398204016417114e-8 2.1657607378172235e-5])

julia> orb
KeplerianElements{Float64, Float64}:
           Epoch :    2.46003e6 (2023-03-24T16:33:40.388)
 Semi-major axis : 7135.79       km
    Eccentricity :    0.00135314
     Inclination :   98.4304     °
            RAAN :  162.113      °
 Arg. of Perigee :   64.9687     °
    True Anomaly :  313.042      °
```
