```
DependentParameters{T <: InfiniteArrayDomain, 
                    M <: NonGenerativeDerivativeMethod} <: InfOptParameter
```

A `DataType` for storing a collection of dependent infinite parameters.

**Fields**

  * `domain::T`: The infinite domain that characterizes the parameters.
  * `supports::Dict{Vector{Float64}, Set{DataType}}`: Support dictionary where keys             are supports and the values are the set of labels for each support.
  * `sig_digits::Int`: The number of significant digits used to round the support values.
  * `derivative_methods::Vector{M}`: The derivative evaluation methods associated with  each parameter.
