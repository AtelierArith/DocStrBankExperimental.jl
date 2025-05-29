```
struct ConstantFESpace <: SingleFieldFESpace
  # private fields
end

ConstantFESpace(model::DiscreteModel; vector_type=Vector{Float64}, field_type=Float64)
ConstantFESpace(trian::Triangulation; vector_type=Vector{Float64}, field_type=Float64)
```

FESpace that is constant over the provided model/triangulation. Typically used as   lagrange multipliers. The kwargs `vector_type` and `field_type` are used to specify the types of the dof-vector and dof-value respectively.
