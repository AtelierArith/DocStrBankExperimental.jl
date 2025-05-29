```
IndependentParameter{T <: InfiniteScalarDomain,
                     M <: AbstractDerivativeMethod,
                     I <: AbstractGenerativeInfo} <: ScalarParameter
```

A `DataType` for storing independent scalar infinite parameters.

**Fields**

  * `domain::T`: The infinite domain that characterizes the parameter.
  * `supports::DataStructures.SortedDict{Float64, Set{DataType}}`: The support points  used to discretize the parameter and their associated type labels stored as  `DataTypes`s which should be a subtype of [`AbstractSupportLabel`](@ref).
  * `sig_digits::Int`: The number of significant digits used to round the support values.
  * `derivative_method::M`: The derivative evaluation method used for derivatives that  are conducted with respect to this parameter.
  * `gnerative_supp_info::I`: The info associated with any generative supports that will   need to be generated for measures and/or derivatives based on existing supports.
