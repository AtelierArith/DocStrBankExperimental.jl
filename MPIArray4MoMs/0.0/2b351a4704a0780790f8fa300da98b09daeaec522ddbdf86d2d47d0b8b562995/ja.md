```
MPIArray{T, I, N, DT, IG}<:AbstractArray{T, N}
```

MoMで使用されるMPIArray。

```
data::DT				ローカルランクに保存されているデータ;
indices::I				グローバル配列における`data`のインデックス
dataOffset::OffsetArray{T, N, DT}	ローカルランクに保存されているデータのOffsetArray
comm::MPI.Comm				`MPI.Comm`
myrank::Int				`MPI.Rank`
size::NTuple{N,Int}			データのグローバルサイズ
rank2indices::Dict{Int, I}		すべてのMPIランクとそのデータのグローバルインデックスを記録する辞書
ghostdata::Array{T, N}			このランクに保存または使用されているデータ
ghostindices::IG			このランクに保存または使用されているghostdataのインデックス
grank2ghostindices::Dict{Int, I}	このランクに保存されていないが使用されているデータ、ここではホストランクとその`ghostdata`におけるインデックスを提供
rrank2localindices::Dict{Int, IG}	このランクにホストされているが他のランクで使用されているデータ、ここではリモートランクと`data`で使用されるインデックスを提供
```
