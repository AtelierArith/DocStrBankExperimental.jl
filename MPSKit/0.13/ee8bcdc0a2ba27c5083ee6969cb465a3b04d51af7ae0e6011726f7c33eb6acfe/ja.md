```
const MultilineMPO = Multiline{<:AbstractMPO}
```

`MPO`オブジェクトの複数行を表す型です。

# コンストラクタ

```
MultilineMPO(mpos::AbstractVector{<:Union{SparseMPO,DenseMPO}})
MultilineMPO(Os::AbstractMatrix{<:MPOTensor})
```

参照: [`Multiline`](@ref), [`AbstractMPO`](@ref)
