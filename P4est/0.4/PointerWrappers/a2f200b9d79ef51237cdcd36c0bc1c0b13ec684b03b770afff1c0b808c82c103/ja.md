```
PointerWrapper(p::Ptr)
```

ポインタ `p` をラップして、基になる `struct` のデータに便利にアクセスします。`struct` のフィールド（または `struct` 自体）は、`[]` を使用して読み書きのためにデリファレンスできます。`struct` に直接 `unsafe_load`/`unsafe_store` を使用するのとは異なり、`[]` 演算子は要求されたフィールドのメモリのみをアクセスするため、単一のフィールドにアクセスする際に全体の `struct` をロード/ストアする必要がなくなります。これは、特にネストされた構造体内のデータにアクセスする際に役立ちます。

### 例

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
