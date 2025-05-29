```
cvar_rbp(B::Vector{Float64}, alpha::Float64, rel_losses::Array{Float64,2}; tol::Float64=1e-6, maxiters::Int=1000)
```

Compute the investment weights on the assets in order to build a CV@R-`alpha` risk budgeting portfolio given risk appetites in `B` and a matrix of relative losses in `rel_losses`. This matrix has size  (|B|, nsamples), so that each column corresponds to a sample of relative losses, and each row to a given asset.

The algorithm stops after reaching a provable optimality gap within (either absolute and relative) tolerance `tol`, or after `maxiters` iterations, if it fails to converge.

Returns (failed, w) :: Bool, Vector{Float64}

For more details on the algorithm, see `cutting_planes_cvar`.
