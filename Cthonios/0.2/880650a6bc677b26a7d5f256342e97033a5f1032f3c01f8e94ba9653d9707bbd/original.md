```julia
struct Section{P, M} <: Cthonios.AbstractSectionInput
```

  * `block_name::String`
  * `q_order::Int64`
  * `physics::Any`
  * `props::Any`

Section inputs. `physics` - Physics object to use in this section. `block_name` - Name of exodus block to construct section from. `q_order` - Quadrature Order to use
