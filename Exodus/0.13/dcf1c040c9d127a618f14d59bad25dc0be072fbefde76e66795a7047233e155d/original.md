```julia
struct SideSet{I, A<:(AbstractVector)} <: Exodus.AbstractExodusSet{I, A<:(AbstractVector)}
```

  * `id::Any`
  * `elements::AbstractVector`
  * `sides::AbstractVector`
  * `num_nodes_per_side::AbstractVector`
  * `side_nodes::AbstractVector`
