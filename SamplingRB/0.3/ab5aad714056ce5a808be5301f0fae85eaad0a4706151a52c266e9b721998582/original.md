```
cutting_planes_evar(B::Vector{Float64}, α::Float64, losses::Array{Float64, 2};
                    tol::Float64=1e-6, maxiters::Int=1000, ub_w::Float64=2000., debug::Int=0, normalize::Bool=true)
```

Compute the investment weights on the assets in order to build an Entropic V@R-alpha  risk budgeting portfolio using a cutting plane method.

The portfolio is such that each asset  j  contributs to the total risk with  B[j], which is also called a  risk appetite.

The algorithm stops after reaching a provable optimality gap within (either absolute or relative) tolerance  tol, or after  maxiters  iterations, if it fails to converge.

In the beginning, the algorithm needs a bounding box for the weights. Since the logarithm already implies w > 0, we use a sufficiently large bound ub_w  for all weights.  If the algorithm converges to a solution that has any weight that large, it should be checked for soundness.  The most common case is when the problem is unbounded below, for example if  alpha  is not large enough.

debug >= 1  prints the iteration numbers, gap and change in the weights. debug >= 2  also prints the current upper and lower bounds and trial points (weights, t) debug >= 3  also prints the risk budgeting constraint and the first-stage status

Returns a triplet (status, weights, t) where the weights sum to one if normalize == true
