```julia
assemble!(
    R::AbstractArray{<:Number},
    Kv::AbstractArray{<:Number},
    R_el::AbstractArray{<:Number},
    Kv_el::AbstractArray{<:Number},
    conn::AbstractArray{<:Integer}
)

```

generic assembly method that directly goes into a vector for doing a residual and matrix vector product at once
