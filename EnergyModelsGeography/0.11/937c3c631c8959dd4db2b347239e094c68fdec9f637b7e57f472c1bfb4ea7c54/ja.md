```
modes_sub(l::Transmission, str::String)
modes_sub(l::Transmission, string_array::Array{String})
modes_sub(ℒᵗʳᵃⁿˢ::Vector{<:Transmission}, str::String)
modes_sub(ℒᵗʳᵃⁿˢ::Vector{<:Transmission}, string_array::Array{String})
```

指定された文字列 `str` または文字列配列 `str_arr` のいずれかの値を名前に含む [`Transmission`](@ref) 回廊 `l` または伝送回廊のベクトル `ℒᵗʳᵃⁿˢ` のすべての [`TransmissionMode`](@ref) を含む配列を返します。
