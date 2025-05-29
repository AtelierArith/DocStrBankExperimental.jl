```
dynamicmodelfit(data::RheoFreqData, model::RheoModelClass; p0::Union{NamedTuple,Nothing} = nothing, lo::Union{NamedTuple,Nothing} = nothing, hi::Union{NamedTuple,Nothing} = nothing, verbose::Bool = false, rel_tol = 1e-4) where T<:Real
```

Fits model to the frequency/loss+storage moduli data.

All arguments are as described below. As this fitting procedure is fitting two functions simultaneously (the storage and loss moduli), if left untransformed the fit would tend to favour the modulus which is larger in magnitude and not fit the other modulus well. To avoid this, RHEOS offers a number of data transforms which can be used by changing `weights` argument.

# Arguments

  * `data`: `RheoFreqData` struct containing all data
  * `model`: `RheoModelClass` containing moduli and symbols of parameters
  * `p0`: Initial parameters to use in fit (uses 0.5 for all parameters if none given)
  * `lo`: Lower bounds for parameters
  * `hi`: Upper bounds for parameters
  * `verbose`: If true, prints parameters on each optimisation iteration
  * `rel_tol_x`: Relative tolerance of optimization for the vector of parameters, see NLOpt docs for more details
  * `rel_tol_f`: Relative tolerance of optimization for the objective function, see NLOpt docs for more details
  * `weights`: Weighting mode for storage and loss modulus (`"none"`, `"mean"`, `"log"`, `"local"` or manually specified)
