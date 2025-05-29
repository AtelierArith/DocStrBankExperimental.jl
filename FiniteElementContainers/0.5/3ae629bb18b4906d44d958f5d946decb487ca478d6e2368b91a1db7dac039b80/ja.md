```julia
assemble!(
    R::AbstractArray{<:Number},
    Kv::AbstractArray{<:Number},
    R_el::AbstractArray{<:Number},
    Kv_el::AbstractArray{<:Number},
    conn::AbstractArray{<:Integer}
)

```

残差と行列ベクトル積を一度に行うためにベクトルに直接入る一般的なアセンブリメソッド
