```
setSurplusRefinement!(tsg::TasmanianSG, tol::Float64; output::Int=-1, refinement_type::AbstractString="", level_limits=Vector{Int32}(undef, 0), scale_correction = Vector{Float64}(undef, 0))
```

using hierarchical surplusses as an error indicator, the surplus refinement adds points to the grid to improve accuracy

when using sequence grids: this algorithm corresponds to the                            greedy Knapsack problem

when using local polynomial or wavelet grids, this call                          corresponds to local spatial refinement

tolerance: float (non-negative)            the relative error tolerance, i.e.,            we refine only for points associated with surplus            that exceeds the tolerance

output: int (indicates the output to use)          selects which output to use for refinement          sequence and local polynomial grids accept -1 to          indicate all outputs

refinement_type: hierarchical and direction refinement strategy                  'classic'  'parents'   'direction'   'fds'   'stable'                  applicable only for Local Polynomial and Wavelet grids

scale*correction: matrix of non-negative numbers                   Instead of comparing the normalized surpluses to                   the tolerance, the scaled surplus will be used.                   The correction allows to manually guide the                   refinement process.                   The surplus of the j-th output of the i-th point                   will be scaled by scale*correction[i][j].                   scale*correction.shape[0] must be equal to                   getNumLoaded()                   If empty, the scale is assumed 1.0                   scale*correction.shape[1] must be equal to the                   number of outputs used in the process, which is                   equal to getNumOutputs() for output == -1,                   or 1 if output > -1.
