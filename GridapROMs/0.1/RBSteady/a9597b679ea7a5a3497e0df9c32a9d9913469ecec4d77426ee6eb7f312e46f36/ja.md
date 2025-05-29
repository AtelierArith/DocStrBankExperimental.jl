```
struct PODProjection <: Projection
  basis::AbstractMatrix
end
```

切断された適正直交分解 [`tpod`](@ref) に由来する射影
