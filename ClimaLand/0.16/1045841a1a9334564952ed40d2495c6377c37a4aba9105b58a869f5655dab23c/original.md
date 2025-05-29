prognostic_vars(m::AbstractModel)

Returns the prognostic variable symbols for the model in the form of a tuple.

Note that this default suggests that a model has no prognostic variables, which is an invalid model setup. This function is meant to be extended for all models.
