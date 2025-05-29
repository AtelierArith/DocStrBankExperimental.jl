SensitivityOp(sensMaps::AbstractMatrix{T}, numContr=1)

builds a `LinearOperator` which performs multiplication of a given image with the coil sensitivities specified in `sensMaps`

# Arguments

  * `sensMaps`    - sensitivity maps ( 1. dim -> voxels, 2. dim-> coils)
  * `numEchoes`   - number of contrasts to which the operator will be applied
