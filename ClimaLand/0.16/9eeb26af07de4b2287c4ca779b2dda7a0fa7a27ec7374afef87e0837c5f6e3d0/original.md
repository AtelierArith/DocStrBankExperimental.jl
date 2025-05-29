prognostic*domain*names(m::AbstractModel)

Returns the domain names for the prognostic variables in the form of a tuple.

Examples: (:surface, :surface, :subsurface).

Note that this default suggests that a model has no prognostic variables, which is an invalid model setup. This function is meant to be extended for all models.
