SensitivityOp(sensMaps::AbstractArray{T,4}, numContr=1)

builds a `LinearOperator` which performs multiplication of a given image with the coil sensitivities specified in `sensMaps`

# Arguments

  * `sensMaps`  - sensitivity maps ( 1.-3. dim -> voxels, 4. dim-> coils)
  * `numContr`  - number of contrasts to which the operator will be applied
