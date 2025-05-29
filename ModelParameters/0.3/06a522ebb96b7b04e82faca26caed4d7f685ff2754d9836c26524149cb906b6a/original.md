Abstract supertype for parameters. Theses are wrappers for model parameter values and  metadata that are returned from [`params`](@ref), and used in  `getfield/setfield/getpropery/setproperty` methods and to generate the Tables.jl interface.  They are stripped from the model with [`stripparams`](@ref).

An `AbstractParam` must define a `Base.parent` method that returns a `NamedTuple`, and a constructor that accepts a `NamedTuple`. It must have a `val` property, and should use `checkhasval` in its constructor.
