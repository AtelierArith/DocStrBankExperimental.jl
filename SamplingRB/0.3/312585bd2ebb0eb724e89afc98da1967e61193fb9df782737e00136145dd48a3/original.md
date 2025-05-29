```
cutting_planes_cvar(B::Vector{Float64}, alpha::Float64, rel_losses::Array{Float64,2};
                    tol::Float64=1e-6, maxiters::Int=1000, ub_w::Float64=2000., debug::Int=0, normalize::Bool=true)
```

Compute the investment weights on the assets in order to build a CV@R-alpha  risk budgeting portfolio using a cutting plane method.

This leads to a decomposition of the simulations of relative losses in  rel_losses in smaller subproblems, and allow us to scale for several thousand realizations. The portfolio is such that each asset  j  contributs to the total risk with  B[j], which is also called a  risk appetite.

The algorithm stops after reaching a provable optimality gap within (either absolute or relative) tolerance  tol, or after  maxiters  iterations, if it fails to converge.

In the beginning, the algorithm needs a bounding box for the weights. Since the logarithm already implies w > 0, we use a sufficiently large bound ub_w  for all weights.  If the algorithm converges to a solution that has any weight that large, it should be checked for soundness.  The most common case is when the problem is unbounded below, for example if  alpha  is not large enough.

debug >= 1  prints the iteration numbers, gap and change in the weights. debug >= 2  also prints the current upper and lower bounds and trial points (weights, V@R) debug >= 3  also prints the risk budgeting constraint and the first-stage status

Returns a triplet (result, weights, V@R-alpha) where the weights sum to one if normalize == true
