```julia
BDDC(operator, injectiontype)
```

BDDC preconditioner for finite element operators

# Arguments:

  * `operator::Operator`:                finite element operator to precondition
  * `injectiontype::BDDCInjectionType`:  type of injection into subassembled space to use

# Returns:

  * BDDC preconditioner object
