This function takes the previous inputs and outputs and assembles a matrix with both excluding jumps.

### Inputs

  * `Inputs` - This is an N x A matrix of previous inputs for which corresponding outputs are available. In this case N is the dimensionality of the fixed point vector that is being sought (and each column is a matrix that is input to the "Function") and A is the number of previous Inputs/Outputs that are being provided to the fixed point.
  * `Outputs` This is a matrix of "Function" values for each column of the "Inputs" matrix.
  * `AgreementThreshold` - A parameter for determining when a column in Inputs and a column in Outputs match. They are deemed to match if the sum of the absolute values of the difference in the columns is less than AgreementThreshold.

### Returns

  * A matrix of inputs and outputs excluding jumps.
