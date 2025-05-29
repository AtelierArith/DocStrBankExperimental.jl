```
struct FixedTable{N, T<:AbstractFloat, AV <: AbstractVector{T}, CL<:Union{Symbol, String}} <: AbstractMatrix{T}
    data::SVector{N, AV}
    cols::SVector{N, CL}
    req_length::Int
    function FixedTable(xs::SVector{N, AV}, cols::SVector{N, CL}, req_length=0) where {T, N, AV<:AbstractVector{T}, CL}
        new{N, T, AV, CL}(xs, cols, req_length)
    end
end
```

これは、列番号 `data[:, 1]` または列名 `data[:, :a]` を介して迅速にアクセスできるように設計された固定幅インターフェースを提供します。`req_length` はオプションのパラメータで、ユーザーが元々要求した長さを指定し、後の関数で FixedTable に行が不足しているかどうかを判断するために使用されます。
