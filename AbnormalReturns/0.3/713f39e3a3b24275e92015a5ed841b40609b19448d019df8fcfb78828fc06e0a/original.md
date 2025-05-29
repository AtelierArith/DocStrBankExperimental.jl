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

This provides a fixed-width interface that is designed to allow quick access (either through accessing a column number `data[:, 1]` or accessing a column name `data[:, :a]`). `req_length` is an optional parameter that specifies the length that a user originally requested, which is used in later functions to determine if the FixedTable has too few rows.
