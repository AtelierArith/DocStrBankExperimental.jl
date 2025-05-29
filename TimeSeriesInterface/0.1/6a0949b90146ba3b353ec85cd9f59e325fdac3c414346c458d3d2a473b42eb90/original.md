FitInput(parameters::Dict{String,Any},              dependent::Vector{TimeSeries{T}},             exogenous::Vector{TimeSeries{T}}) where T

FitInput is the only information needed by Fit Functions Fit Functions will just use dependent, exogenous and parameters All extra information passed to the Fit Function that is not the dataset must be inside the parameters Dict. You can also include keys 'args' ands 'kwargs' inside the dictionary and they will be passed directly to the FitFunction
