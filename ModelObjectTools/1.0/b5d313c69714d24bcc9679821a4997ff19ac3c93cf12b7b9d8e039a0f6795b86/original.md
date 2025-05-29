modelObjectFromVector(baseType::Type, vectorInput::AbstractArray{<:Real},         fields = fieldnames(baseType))

Constructs a model object based a vector of transformed  parameter values created by the vectorRepresentation() function. The specific parameters being modified are given by the fields input. Other parameters come from the the default values for type baseType.
