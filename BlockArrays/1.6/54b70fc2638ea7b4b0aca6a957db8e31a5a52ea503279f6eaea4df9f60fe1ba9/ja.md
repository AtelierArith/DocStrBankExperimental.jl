```
BlockArray{T, N, R<:AbstractArray{<:AbstractArray{T,N},N}, BS<:Tuple{Vararg{AbstractUnitRange{<:Integer},N}}} <: AbstractBlockArray{T, N}
```

`BlockArray`は、各ブロックが連続して格納される配列です。これは、ブロックの挿入や取得が非常に高速で、データのコピーが不要なため、メモリの割り当てが発生しないことを意味します。

型定義において、`R`はブロックを保持する配列の型を定義します。例えば、`Matrix{Matrix{Float64}}`のようになります。
