```
GlobalPencilArray{T,N} <: AbstractArray{T,N}
```

[`PencilArray`](@ref)をラップする`OffsetArray`のエイリアスです。

`PencilArray`とは異なり、`GlobalPencilArray`は*グローバル*インデックスを使用します。これは一般に、特定のMPIプロセスに対して1から始まらないことがあります。

`GlobalPencilArray`を`PencilArray`から作成するには、[`global_view`](@ref)関数を使用する必要があります。
