```
AAAeigs([eltype,] nep::NEP, Z::AbstractArray{T}; [logger=0,][mmax=100,][neigs=6,][maxit=min(max(10*neigs,30),100),][shifts=Vector{T}(),][linsolvercreator=FactorizeLinSolverCreator(max_factorizations=min(length(unique(shifts)),10)),][tol=eps(real(T))*1e6,][tol_appr=eps(real(T))*1e3,][v0=Vector{T}(),][errmeasure=ResidualErrmeasure(nep),][weighted=false,][cleanup_appr=true,][tol_cln=min(eps(real(T)),tol_appr),][return_details=false,][check_error_every=10,][inner_logger=0])
```

Find a few eigenvalues and eigenvectors of a nonlinear eigenvalue problem, using the `AAAeigs` algorithm.

# Arguments

  * `nep`: An instance of a nonlinear eigenvalue problem has to be of type `AbstractSPMF`
  * `Z`: An array containing the sample domain of the nep, given as a series of points.
  * `mmax`: Max degree of AAA-approximation.
  * `neigs`: Number of eigenvalues to find.
  * `maxit`: Max number of total iterations.
  * `shifts`: L vector of shifts used during the Krylov routine (empty -> shift=0)
  * `tol`: Tolerance for residual.
  * `tol_appr`: Tolerance for convergence of AAA-approximation.
  * `v0`: Starting vector.
  * `weighted`: Wether to use Weighted or Set-Valued AAA.
  * `cleanup_appr`: Whether to detect spurious poles in AAA.
  * `tol_cln`: Tolerance for cleanup of spurious poles.
  * `return_details`: Whether to return solution details (see `AAASolutionDetails`).
  * `check_error_every`: Check for convergence / termination every this number of iterations.
  * `inner_logger`: Works in the same way as logger but for the AAA rational approximation (see `svAAA`)

See [`augnewton`](@ref) for other parameters.

# Return values

  * `Λ`: Vector of eigenvalues of the nonlinear eigenvalue problem inside the sample set Z.
  * `X`: Corresponding matrix of eigenvectors.
  * `res`: Corresponding residuals.
  * `details`: Solution details, if requested (see AAASolutionDetails).

# Example

```julia-repl
julia> Random.seed!(2022);
julia> nep=nep_gallery("nlevp_native_gun");
julia> m=250^2; r=300^2-200^2;
julia> Z=m-r.+2*r*rand(1000)+im*(rand(1000)*r.+sqrt(1e-13));
julia> Z=Z[(~).(imag.(Z).>sin.(acos.((real.(Z).-m)/r))*r.-sqrt(1e-13))];
julia> Z=[transpose([LinRange(m-r+1e-2,m+r-1e-2,250)' m-r.+2*r*(exp.(im*LinRange(0,pi,250)')/2 .+.5)]); Z[1:500]];
julia> shifts=r*[2/3,(1+im)/3,0,(-1+im)/3,-2/3].+m;
julia> λ,X=AAAeigs(nep,Z,shifts=shifts);
julia> [norm(compute_Mlincomb(nep,λ[i],X[:,i]))/norm(X[:,i]) for i=1:length(λ)]
6-element Vector{Float64}:
 5.282105614825289e-12
 1.675900913610527e-11
 4.971723316733914e-11
 9.437128735632508e-11
 1.2277986011104446e-10
 1.4546362158344052e-10
```

# References

  * P. Lietaert, J. Pérez, B. Vandereycken, and K. Meerbergen. Automatic rational approximation and linearization of nonlinear eigenvalue problems. IMA journal of numerical analysis, 2018.
  * R. Van Beeumen, K. Meerbergen, and W. Michiels. Compact rational Krylov methods for nonlinear eigenvalue problems. SIAM Journal on Matrix Analysis and Applications, 36(2):820-838, 2015.
