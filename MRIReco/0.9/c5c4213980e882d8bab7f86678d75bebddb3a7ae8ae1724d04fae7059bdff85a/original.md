Performs iterative image reconstruction independently for the data of all coils, contrasts and slices

# Arguments

  * `acqData::AcquisitionData`            - AcquisitionData object
  * `reconSize::NTuple{2,Int64}`              - size of image to reconstruct
  * `reg::Vector{<:AbstractRegularization}`                 - Regularization to be used
  * `sparseTrafo::AbstractLinearOperator` - sparsifying transformation
  * `weights::Vector{Vector{Complex{<:AbstractFloat}}}` - sampling density of the trajectories in acqData
  * `solver::Type{<:AbstractLinearSolver}`                  - name of the solver to use
  * (`normalize::Bool=false`)             - adjust regularization parameter according to the size of k-space data
  * (`params::Dict{Symbol,Any}`)          - Dict with additional parameters
