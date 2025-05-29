```julia
struct Block{I, A<:(AbstractMatrix)} <: Exodus.AbstractExodusSet{I, A<:(AbstractMatrix)}
```

  * `id::Any`
  * `num_elem::Int64`
  * `num_nodes_per_elem::Int64`
  * `elem_type::String`
  * `conn::AbstractMatrix`
