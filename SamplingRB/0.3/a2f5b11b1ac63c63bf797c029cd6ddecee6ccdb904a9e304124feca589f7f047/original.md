```
cutting_planes(B::Vector{Float64}, rel_losses::Array{Float64,2},
               risk_measure::AbstractRiskMeasure;
               tol::Float64=1e-6, maxiters::Int=1000, ub_w::Float64=2000., debug::Int=0, normalize::Bool=true)
```

Compute the investment weights on the assets in order to build a risk budgeting portfolio using a cutting plane method. The portfolio is such that each asset  j  contributs to the total risk with  B[j], which is also called a  risk appetite.

If the evaluation of the Risk Measure is efficient, this scales to several thousand realizations of the simulations of relative losses.

The algorithm stops after reaching a provable optimality gap within (either absolute or relative) tolerance  tol, or after  maxiters  iterations, if it fails to converge.

In the beginning, the algorithm needs a bounding box for the weights. Since the logarithm already implies w > 0, we use a sufficiently large bound ub_w  for all weights.  If the algorithm converges to a solution that has any weight that large, it should be checked for soundness.  The most common case is when the problem is unbounded below, for example if the risk measure is too conservative.

debug >= 1  prints the iteration numbers, gap and change in the weights. debug >= 2  also prints the current upper and lower bounds and trial weights. debug >= 3  also prints the risk budgeting constraint and the first-stage status

Returns a tuple (result, weights) where the weights sum to one if normalize == true
