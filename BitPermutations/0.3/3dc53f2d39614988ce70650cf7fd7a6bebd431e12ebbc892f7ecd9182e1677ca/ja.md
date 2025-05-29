```
BitPermutation{T}([backend_type], p::AbstractVector{Int}; [...])
```

順列ベクトル `p` から `BitPermutation{T}` を構築します。実際に順列を実行するバックエンドは、オプションで `backend_type` (`<:PermutationBackend`) を指定することで設定できます。デフォルトは以下の通りです：

  * AVX-512 命令が利用可能な場合、`T<:Union{UInt16,UInt32,UInt64}` に対して `AVXCopyGather` が選択されます；
  * BMI2 命令が利用可能な場合、`T<:Union{UInt32,UInt64}` に対して `GRPNetwork` が選択されます；
  * その他の場合は、`BenesNetwork` が使用されます。

追加のキーワード引数はバックエンドに渡されます。

参照： [`BenesNetwork`](@ref), [`GRPNetwork`](@ref), [`AVXCopyGather`](@ref).
