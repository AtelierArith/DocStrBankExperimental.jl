```
struct MultiFieldFESpace{S<:MultiFieldStyle,B} <: FESpace
  spaces::Vector{<:SingleFieldFESpace}
  multi_field_style::S
  constraint_style::Val{B}
end
```
