```
process(self::HMM, d::Array{T, 2}, splitSw::Bool;
params::HMMParams) where T <: Number
```

# Description

Process hidden Markov model object. Meant as an iterative mutating function, perform several steps:

  * reset model traceback.
  * feed frames into model data.
  * update model.
  * generate hypothesized new states.

See also: [`setup`](@ref), [`HMM`](@ref), [`HMMParams`](@ref)
