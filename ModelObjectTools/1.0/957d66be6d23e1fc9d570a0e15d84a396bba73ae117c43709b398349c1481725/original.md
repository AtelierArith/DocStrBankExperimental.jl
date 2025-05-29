modelObjectFromVector(base, vectorInput::AbstractArray{<:Real},         fields = fieldnames(typeof(base)))

Constructs a model object based a vector of transformed  parameter values created by the vectorRepresentation() function. The specific parameters being modified are given by the fields input. Other parameters come from the base input.
