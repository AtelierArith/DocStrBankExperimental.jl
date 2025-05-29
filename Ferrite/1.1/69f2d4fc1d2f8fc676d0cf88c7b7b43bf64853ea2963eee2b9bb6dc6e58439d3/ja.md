```
dof_range(sdh::SubDofHandler, field_idx::Int)
dof_range(sdh::SubDofHandler, field_name::Symbol)
dof_range(dh:DofHandler, field_name::Symbol)
```

指定されたフィールドのローカルdof範囲を返します。フィールドはその名前またはインデックスで指定でき、`field_idx`は`SubDofHandler`内のフィールドのインデックスを表し、`field_idxs`は`DofHandler`内の`SubDofHandler`インデックスと`field_idx`のタプルです。

!!! note
    フィールドの`dof_range`は異なる`SubDofHandler`間で異なる場合があります。したがって、複数の`SubDofHandler`が存在する場合は、`field_idxs`を使用するか、特定の`SubDofHandler`を直接参照することをお勧めします。`field_name`を使用すると、常に`DofHandler`内の`field`の最初の出現を参照します。


例:

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
