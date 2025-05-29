```julia
struct ContResult{Tkind<:BifurcationKit.AbstractContinuationKind, Tbr, Teigvals, Teigvec, Biftype, Tsol, Tparc, Tprob, Talg} <: BifurcationKit.AbstractResult{Tkind<:BifurcationKit.AbstractContinuationKind, Tprob}
```

Structure which holds the results after a call to [`continuation`](@ref).

You can see the propertynames of a result `br` by using `propertynames(br)` or `propertynames(br.branch)`.

# Fields

  * `branch::StructArrays.StructArray`: holds the low-dimensional information about the branch. More precisely, `branch[i+1]` contains the following information `(record_from_solution(u, param), param, itnewton, itlinear, ds, θ, n_unstable, n_imag, stable, step)` for each continuation step `i`.

      * `itnewton` number of Newton iterations
      * `itlinear` total number of linear iterations during newton (corrector)
      * `n_unstable` number of eigenvalues with positive real part for each continuation step (to detect stationary bifurcation)
      * `n_imag` number of eigenvalues with positive real part and non zero imaginary part at current continuation step (useful to detect Hopf bifurcation).
      * `stable` stability of the computed solution for each continuation step. Hence, `stable` should match `eig[step]` which corresponds to `branch[k]` for a given `k`.
      * `step` continuation step (here equal `i`)
  * `eig::Array{@NamedTuple{eigenvals::Teigvals, eigenvecs::Teigvec, converged::Bool, step::Int64}, 1} where {Teigvals, Teigvec}`: A vector with eigen-elements at each continuation step.
  * `sol::Any`: Vector of solutions sampled along the branch. This is set by the argument `save_sol_every_step::Int64` (default 0) in [`ContinuationPar`](@ref).
  * `contparams::Any`: The parameters used for the call to `continuation` which produced this branch. Must be a [`ContinuationPar`](@ref)
  * `kind::BifurcationKit.AbstractContinuationKind`: Type of solutions computed in this branch. Default: EquilibriumCont()
  * `prob::Any`: Bifurcation problem used to compute the branch, useful for branch switching. For example, when computing periodic orbits, the functional `PeriodicOrbitTrapProblem`, `ShootingProblem`... will be saved here. Default: nothing
  * `specialpoint::Vector`: A vector holding the list of detected bifurcation points. See [`SpecialPoint`](@ref) for a list of special points.
  * `alg::Any`: Continuation algorithm used for the computation of the branch

# Associated methods

  * `length(br)` number of the continuation steps
  * `show(br)` display information about the branch
  * `propertynames(br)` give the propertynames of a result
  * `eigenvals(br, ind)` returns the eigenvalues for the ind-th continuation step
  * `eigenvec(br, ind, indev)` returns the indev-th eigenvector for the ind-th continuation step
  * `get_normal_form(br, ind)` compute the normal form of the ind-th points in `br.specialpoint`
  * `getlens(br)` return the parameter axis used for the branch
  * `getlenses(br)` return the parameter two axis used for the branch when 2 parameters continuation is used (Fold, Hopf, NS, PD)
  * `get_solx(br, k)` returns the k-th solution on the branch
  * `get_solp(br, k)` returns the parameter  value associated with k-th solution on the branch
  * `getparams(br)` Parameters passed to continuation and used in the equation `F(x, par) = 0`.
  * `getparams(br, ind)` Parameters passed to continuation and used in the equation `F(x, par) = 0` for the ind-th continuation step.
  * `setparam(br, p0)` set the parameter value `p0` according to `::Lens` for the parameters of the problem `br.prob`
  * `getlens(br)` get the lens used for the computation of the branch
  * `eigenvals(br, ind)` give the eigenvalues at continuation step `ind`
  * `eigenvalsfrombif(br, ind)` give the eigenvalues at bifurcation point index `ind`
  * `type(br, ind)` returns the type of the ind-th bifurcation point
  * `br[k+1]` gives information about the k-th step. A typical run yields the following

```
julia> br[1]
(x = 0.0, param = 0.1, itnewton = 0, itlinear = 0, ds = -0.01, θ = 0.5, n_unstable = 2, n_imag = 2, stable = false, step = 0, eigenvals = ComplexF64[0.1 - 1.0im, 0.1 + 1.0im], eigenvecs = ComplexF64[0.7071067811865475 - 0.0im 0.7071067811865475 + 0.0im; 0.0 + 0.7071067811865475im 0.0 - 0.7071067811865475im])
```

which provides the value `param` of the parameter of the current point, its stability, information on the newton iterations, etc. The fields can be retrieved using `propertynames(br.branch)`. This information is stored in `br.branch` which is a `StructArray`. You can thus extract the vector of parameters along the branch as

```
julia> br.param
10-element Vector{Float64}:
 0.1
 0.08585786437626905
 0.06464466094067263
 0.03282485578727799
-1.2623798512809007e-5
-0.07160718539365075
-0.17899902778635765
-0.3204203840236672
-0.4618417402609767
-0.5
```

  * `continuation(br, ind)` performs automatic branch switching (aBS) from ind-th bifurcation point. Typically branching from equilibrium to equilibrium, or periodic orbit to periodic orbit.
  * `continuation(br, ind, lens2)` performs two parameters `(getlens(br), lens2)` continuation of the  ind-th bifurcation point.
  * `continuation(br, ind, probPO::AbstractPeriodicOrbitProblem)` performs aBS from ind-th bifurcation point (which must be a Hopf bifurcation point) to branch of periodic orbits.
