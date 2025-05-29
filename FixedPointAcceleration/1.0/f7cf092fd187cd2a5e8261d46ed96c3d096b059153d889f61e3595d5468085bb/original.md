```
fixed_point_new_input(Inputs::AbstractArray{T,2}, Outputs::AbstractArray{T,2}, Algorithm::Symbol = :Anderson;
                           MaxM::Integer = 10, SimpleStartIndex::Integer = 1, ExtrapolationPeriod::Integer = 1, Dampening::S = AbstractFloat(1),
                           ConditionNumberThreshold::R = AbstractFloat(1000), PrintReports::Bool = false, ReplaceInvalids::InvalidReplacement = :NoAction) where R<:Real where S<:Real where T<:Real
```

This function takes the previous inputs and outputs from the fixed_point function and determines what vector to try next in seeking a fixed point.

### Inputs

  * `Inputs` - This is an N x A matrix of previous inputs for which corresponding outputs are available. In this case N is the dimensionality of the fixed point vector that is being sought (Hence each column is a matrix that is input to the "Function") and A is the number of previous Inputs/Outputs that are being provided to the fixed point.
  * `Outputs` - This is a matrix of Function values for the each column of the `Inputs` matrix.
  * `Algorithm` - This is the fixed point Algorithm to be used. It can be "Anderson", "Simple", "Aitken", "Newton", "MPE", "RRE", "VEA", "SEA".
  * `MaxM` - This is the number of saved iterates that are used in the Anderson algorithm. This has no role if another Algorithm is used.
  * `SimpleStartIndex` - This is the index for what column in the input/output matrices did the algorithm start doing simple iterates without jumps. This is used for all Algorithms except the simple and Anderson Algorithms where it has no effect.
  * `ExtrapolationPeriod` - This is the number of simple iterates to perform before extrapolating. This is used for the MPE, RRE, VEA and SEA Algorithms and has no effect if another Algorithm is chosen.
  * `Dampening` - This is the dampening parameter. By default it is 1 which means no dampening takes place. It can also be less than 1 (indicating dampening) or more than 1 (indicating extrapolation).
  * `ConditionNumberThreshold` - This is what threshold should be chosen to drop previous iterates if the matrix is ill conditioned. Only used in Anderson acceleration.
  * `PrintReports` - This is a boolean describing whether to print ongoing ConvergenceMetric values for each iterate.

### Returns

  * A `Vector` of the next guess for the fixed point.

### Examples

```
FPFunction = function(x){c(0.5*sqrt(abs(x[1] + x[2])), 1.5*x[1] + 0.5*x[2])}
A = fixed_point( Function = FPFunction, Inputs = [0.3,900], MaxIter = 6, Algorithm = :Simple)
NewGuessAnderson = fixed_point_new_input(A[:Inputs], A[:Outputs], Algorithm = :Anderson)
NewGuessVEA = fixed_point_new_input(A[:Inputs], A[:Outputs], Algorithm = :VEA)
NewGuessMPE = fixed_point_new_input(A[:Inputs], A[:Outputs], Algorithm = :MPE)
NewGuessAitken = fixed_point_new_input(A[:Inputs], A[:Outputs], Algorithm = :Aitken)
```
