```
dof_range(sdh::SubDofHandler, field_idx::Int)
dof_range(sdh::SubDofHandler, field_name::Symbol)
dof_range(dh:DofHandler, field_name::Symbol)
```

Return the local dof range for a given field. The field can be specified by its name or index, where `field_idx` represents the index of a field within a `SubDofHandler` and `field_idxs` is a tuple of the `SubDofHandler`-index within the `DofHandler` and the `field_idx`.

!!! note
    The `dof_range` of a field can vary between different `SubDofHandler`s. Therefore, it is advised to use the `field_idxs` or refer to a given `SubDofHandler` directly in case several `SubDofHandler`s exist. Using the `field_name` will always refer to the first occurrence of `field` within the `DofHandler`.


Example:

```jldoctest
julia> grid = generate_grid(Triangle, (3, 3))
Grid{2, Triangle, Float64} with 18 Triangle cells and 16 nodes

julia> dh = DofHandler(grid); add!(dh, :u, 3); add!(dh, :p, 1); close!(dh);

julia> dof_range(dh, :u)
1:9

julia> dof_range(dh, :p)
10:12

julia> dof_range(dh, (1,1)) # field :u
1:9

julia> dof_range(dh.subdofhandlers[1], 2) # field :p
10:12
```
