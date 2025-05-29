```
ParameterProfiles(DM::AbstractDataModel, Confnum::Real=2, Inds::AbstractVector{<:Int}=1:pdim(DM); adaptive::Bool=true, N::Int=31, plot::Bool=isloaded(:Plots), SaveTrajectories::Bool=true, IsCost::Bool=true, parallel::Bool=true, dof::Int=DOF(DM), kwargs...)
```

Computes the profile likelihood for components `Inds` of the parameters $θ \in \mathcal{M}$ over the given `Domain`. Returns a vector of matrices where the first column of the n-th matrix specifies the value of the n-th component and the second column specifies the associated confidence level of the best fit configuration conditional to the n-th component being fixed at the associated value in the first column. `Confnum` specifies the confidence level to which the profile should be computed if possible with `Confnum=2` corresponding to 2σ, i.e. approximately 95.4%. Single profiles can be accessed via `P[i]`, given a profile object `P`.

The kwarg `IsCost=true` can be used to skip the transformation from the likelihood values to the associated confidence level such that `2(LogLikeMLE(DM) - loglikelihood(DM, θ))` is returned in the second columns of the profiles. The trajectories followed during the reoptimization along the profile can be saved via `SaveTrajectories=true`. For `adaptive=false` the size of the domain is estimated from the inverse Fisher metric and the profile is evaluated on a fixed stepsize grid. Further `kwargs` can be passed to the optimization.

# Extended help

For visualization of the results, multiple methods are available, see e.g. [`PlotProfileTrajectories`](@ref), [`PlotRelativeParameterTrajectories`](@ref).
