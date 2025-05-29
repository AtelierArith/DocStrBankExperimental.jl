```julia
struct SpecialPoint{T, Tp, Tv, Tvτ} <: BifurcationKit.AbstractBifurcationPoint
```

Structure to record special points on a curve. There are two types of special points that are recorded in this structure: bifurcation points and events (see https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/EventCallback/).

## Associated methods

  * `BifurcationKit.type(::SpecialPoint)` returns the bifurcation type (`::Symbol`)

  * `type::Symbol`: Description of the special points. In case of Events, this field records the user passed named to the event, or the default `:userD`, `:userC`. In case of bifurcation points, it can be one of the following:

    ```
    - :bp Bifurcation point, simple eigenvalue crossing the imaginary axis
    - :fold Fold point
    - :hopf Hopf point
    - :nd not documented bifurcation point. Detected by multiple eigenvalues crossing. Generally occurs in problems with symmetries or in cases where the continuation step size is too large and merge two different bifurcation points.
    - :cusp Cusp point
    - :gh Generalized Hopf point (also called Bautin point)
    - :bt Bogdanov-Takens point
    - :zh Zero-Hopf point
    - :hh Hopf-Hopf point
    - :ns Neimark-Sacker point
    - :pd Period-doubling point
    - :R1 Strong resonance 1:1 of periodic orbits
    - :R2 Strong resonance 1:2 of periodic orbits
    - :R3 Strong resonance 1:3 of periodic orbits
    - :R4 Strong resonance 1:4 of periodic orbits
    - :foldFlip Fold / Flip of periodic orbits
    - :foldNS Fold / Neimark-Sacker of periodic orbits
    - :pdNS  Period-Doubling / Neimark-Sacker of periodic orbits
    - :gpd Generalized Period-Doubling of periodic orbits
    - :nsns Double Neimark-Sacker of periodic orbits
    - :ch Chenciner bifurcation of periodic orbits
     Default: :none
    ```
  * `idx::Int64`: Index in `br.branch` or `br.eig` (see [`ContResult`](@ref)) for which the bifurcation occurs. Default: 0
  * `param::Any`: Parameter value at the special point (this is an estimate). Default: 0.0
  * `norm::Any`: Norm of the equilibrium at the special point Default: 0.0
  * `printsol::Any`: `printsol = record_from_solution(x, param)` where `record_from_solution` is one of the arguments to [`continuation`](@ref) Default: 0.0
  * `x::Any`: Equilibrium at the special point Default: Vector{T}(undef, 0)
  * `τ::BifurcationKit.BorderedArray{Tvτ, T} where {T, Tvτ}`: Tangent along the branch at the special point Default: BorderedArray(x, T(0))
  * `ind_ev::Int64`: Eigenvalue index responsible for detecting the special point (if applicable) Default: 0
  * `step::Int64`: Continuation step at which the special occurs Default: 0
  * `status::Symbol`: `status ∈ {:converged, :guess, :guessL}` indicates whether the bisection algorithm was successful in detecting the special (bifurcation) point. If `status == :guess`, the bisection algorithm failed to meet the requirements given in `::ContinuationPar`. Same for `status == :guessL` but the bisection algorithm stopped on the left of the bifurcation point. Default: :guess
  * `δ::Tuple{Int64, Int64}`: `δ = (δr, δi)` where δr indicates the change in the number of unstable eigenvalues and δi indicates the change in the number of unstable eigenvalues with nonzero imaginary part. `abs(δr)` is thus an estimate of the dimension of the kernel of the Jacobian at the special (bifurcation) point. Default: (0, 0)
  * `precision::Any`: Precision in the location of the special point Default: -1
  * `interval::Tuple{T, T} where T`: Interval parameter containing the special point Default: (0, 0)
