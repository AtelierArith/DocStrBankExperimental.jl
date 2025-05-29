```
MPIArray{T, I, N, DT, IG}<:AbstractArray{T, N}
```

MPIArray used in MoM.

```
data::DT				the data stored in local rank;
indices::I				indice of `data` in global Array
dataOffset::OffsetArray{T, N, DT}	the OffsetArray of data stored in local rank
comm::MPI.Comm				`MPI.Comm`
myrank::Int				`MPI.Rank`
size::NTuple{N,Int}			global size of data
rank2indices::Dict{Int, I}		a dict record all MPI ranks to their datas global indices
ghostdata::Array{T, N}			the data stored or used in this rank
ghostindices::IG			the indices of ghostdata stored or used in this rank
grank2ghostindices::Dict{Int, I}	the data used but not stored in this rank, here provides the host rank and its indices in `ghostdata`
rrank2localindices::Dict{Int, IG}	the data host in this rank but used in other rank, here provides the remote rank and the indices used in `data`
```
