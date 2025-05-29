mergeInputParams(inputparams1::T, inputparams2::T; warn = false) where {T <: DictInputParams}

# Arguments

  * `inputparams1  ::T` : First input parameter structure
  * `inputparams2  ::T` : Second input parameter structure
  * `warn = false` : If option `warn` is true, then give a warning when two distinct values are given for the same field. The first value has other precedence.

# Returns

A `DictInputParams` structure whose field are the composition of the two input parameter structures.
