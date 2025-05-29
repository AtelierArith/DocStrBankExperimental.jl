```julia
read_from_txt(
    file_name::String
) -> Tuple{Vector{Array{Float64}}, Vector{Float64}}

```

ファイルからノード座標と有限要素係数ベクトルを読み込みます。ファイルは[write*to*txt](@ref)によって生成されます。
