```
UniformGenerativeInfo <: AbstractGenerativeInfo
```

A `DataType` for generative supports that will be generated in a uniform manner  over finite elements (i.e., in between the existing supports). These generative  supports are described by the `support_basis` which lie in a nominal domain [0, 1].  The constructor is of the form:

```
    UniformGenerativeInfo(support_basis::Vector{<:Real}, label::DataType, 
                          [lb::Real = 0, ub::Real = 1])
```

where the `support_basis` is defined over [`lb`, `ub`].

**Fields**

  * `support_basis::Vector{Float64}`: The basis of generative supports defined in   [0, 1] that will be transformed for each finite element.
  * `label::DataType`: The unique label to be given to each generative support.
