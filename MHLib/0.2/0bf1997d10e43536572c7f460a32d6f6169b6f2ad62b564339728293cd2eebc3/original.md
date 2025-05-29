```
VectorSolution
```

An abstract solution encoded by a vector of elements with type `T`.

Concrete subtypes need to implement:

  * all requirements of the supertype `Solution`
  * `x::AbstractVector`: vector representing the solution
  * `destroyed::Union{Nothing, Int[]}`: vector of positions of destroyed elements when    using destroy+repair operators e.g. in LNS
