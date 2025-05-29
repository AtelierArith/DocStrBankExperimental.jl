```
GenerateBoundary(DM::DataModel, u0::AbstractVector{<:Number}; tol::Real=1e-9, meth=Tsit5(), mfd::Bool=true) -> ODESolution
```

Basic method for constructing a curve lying on the confidence region associated with the initial configuration `u0`.
