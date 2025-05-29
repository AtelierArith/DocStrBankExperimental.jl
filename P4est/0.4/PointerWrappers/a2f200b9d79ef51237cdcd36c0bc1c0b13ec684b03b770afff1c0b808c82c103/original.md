```
PointerWrapper(p::Ptr)
```

Wrap the pointer `p` to conveniently access the data of the underlying `struct`. Fields of the `struct` (or the `struct` itself) can be dereferenced for reading/writing using `[]`. As opposed to using `unsafe_load`/`unsafe_store` on the `struct` directly, the `[]` operator only accesses the memory for the requested field, thereby avoiding to having to load/store the entire struct when accessing only a single field. This can be helpful especially when accessing data in nested structures.

### Example

```repl
julia> using P4est, MPI

julia> MPI.Init()
MPI.ThreadLevel(2)

julia> connectivity = p4est_connectivity_new_brick(2, 2, 0, 0)
Ptr{p4est_connectivity} @0x000060000378b010

julia> p4est = p4est_new_ext(MPI.COMM_WORLD, connectivity, 0, 0, true, 0, C_NULL, C_NULL)
Into p4est_new with min quadrants 0 level 0 uniform 1
New p4est with 4 trees on 1 processors
Initial level 0 potential global quadrants 4 per tree 1
Done p4est_new with 4 total quadrants
Ptr{P4est.LibP4est.p4est} @0x0000600002b9d7b0

julia> p4est_pw = PointerWrapper(p4est)
PointerWrapper{P4est.LibP4est.p4est}(Ptr{P4est.LibP4est.p4est} @0x0000600002b9d7b0)

julia> p4est_pw.connectivity.num_trees[]
4
```
