```julia
DiscreteUpdate(t; dt)

```

離散更新（シフト）演算子を表し、その意味は

```
DiscreteUpdate(t; dt=0.01)(y) ~ y(t+dt)
```

# 例

```jldoctest
julia> using Symbolics

julia> @variables t;

julia> U = DiscreteUpdate(t; dt=0.01)
(::Difference) (generic function with 2 methods)
```
