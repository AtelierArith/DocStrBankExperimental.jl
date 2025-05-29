Abstract type for all variables in Jutul.

A variable is associated with a [`JutulEntity`](@ref) through the [`associated_entity`](@ref) function. A variable is local to that entity, and cannot depend on other entities. Variables are used by models to define:

  * primary variables: Sometimes referred to as degrees of freedom, primary unknowns or solution variables
  * parameters: Static quantities that impact the solution
  * secondary variables: Can be computed from a combination of other primary and secondary variables and parameters.
