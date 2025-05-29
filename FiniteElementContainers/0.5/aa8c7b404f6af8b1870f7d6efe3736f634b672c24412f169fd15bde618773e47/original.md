```julia
assemble!(
    R::AbstractArray{<:Number},
    R_el::AbstractArray{<:Number},
    conn::AbstractArray{<:Integer}
)

```

generic assembly method that directly goes into a vector
