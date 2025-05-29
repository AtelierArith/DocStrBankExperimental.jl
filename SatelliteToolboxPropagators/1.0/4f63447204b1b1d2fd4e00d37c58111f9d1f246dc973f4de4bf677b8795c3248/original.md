```
fit_j2_mean_elements(vjd::AbstractVector{Tjd}, vr_i::AbstractVector{Tv}, vv_i::AbstractVector{Tv}; kwargs...) where {Tjd<:Number, Tv<:AbstractVector} -> KeplerianElements{Float64, Float64}, SMatrix{6, 6, Float64}
```

Fit a set of mean Keplerian elements for the J2 orbit propagator using the osculating elements represented by a set of position vectors `vr_i` [m] and a set of velocity vectors `vv_i` [m / s] represented in an inertial reference frame at instants in the array `vjd` [Julian Day].

!!! note
    This algorithm version will allocate a new J2 propagator with the default constants `j2c_egm2008`. If another set of constants are required, use the function [`fit_j2_mean_elements!`](@ref) instead.


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

  * `KeplerianElements{Float64, Float64}`: Fitted Keplerian elements.
  * `SMatrix{6, 6, Float64}`: Final covariance matrix of the least-square algorithm.

# Examples

```julia-repl
julia> vr_i = [
           [-6792.402703741442, 2192.6458461287293, 0.18851758695295118]  .* 1000,
           [-1781.214419290065, 1619.7795321872854, 6707.771633846665]    .* 1000,
           [ 5693.643675547716, -1192.342828671633, 4123.976025977494]    .* 1000,
           [ 5291.613719530499, -2354.5417593130833, -4175.561367156414]  .* 1000,
           [-2416.3705905186903, -268.74923235392623, -6715.411357310478] .* 1000,
           [-6795.043410709359, 2184.4414321930635, -0.4327055325971031]  .* 1000,
       ];

julia> vv_i = [
           [0.3445760107690598, 1.0395135806993514, 7.393686131436984]    .* 1000,
           [6.875680282038698, -1.864319399615942, 2.270603214569518]     .* 1000,
           [3.8964090757666496, -2.1887896252945875, -5.9960180359219075] .* 1000,
           [-4.470258022565413, 0.5119576359985208, -5.9608372367141635]  .* 1000,
           [-6.647358060413909, 2.495415251255861, 2.292118747543002]     .* 1000,
           [0.3427096905434428, 1.040125572862349, 7.3936887585116855]    .* 1000,
       ];

julia> vjd = [
           2.46002818657856e6
           2.460028200467449e6
           2.460028214356338e6
           2.4600282282452267e6
           2.4600282421341157e6
           2.4600282560230047e6
       ];

julia> orb, P = fit_j2_mean_elements(vjd, vr_i, vv_i)
ACTION:   Fitting the mean elements for the J2 propagator.
           Iteration        Position RMSE        Velocity RMSE           Total RMSE       RMSE Variation
                                     [km]             [km / s]                  [ ]
PROGRESS:         23               4.3413           0.00540076              4341.31         -2.90721e-06 %

(KeplerianElements{Float64, Float64}: Epoch = 2.46003e6 (2023-03-24T18:08:40.388), [0.16604846233666615 0.06643574144803302 … -3.85541368066423e-5 0.000124032254172014; 0.0664357414470214 0.26633448262787296 … -1.7943612056596758e-5 -1.9567956793856743e-5; … ; -3.855413680493565e-5 -1.7943612058983507e-5 … 4.3971984339116176e-7 -8.092704691911699e-8; 0.0001240322541726098 -1.9567956793417353e-5 … -8.092704692135158e-8 1.2451922454639337e-7])

julia> orb
KeplerianElements{Float64, Float64}:
           Epoch :    2.46003e6 (2023-03-24T18:08:40.388)
 Semi-major axis : 7131.63       km
    Eccentricity :    0.00114299
     Inclination :   98.4366     °
            RAAN :  162.177      °
 Arg. of Perigee :  101.286      °
    True Anomaly :  258.689      °
```
