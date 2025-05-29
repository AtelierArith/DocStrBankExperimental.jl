```
modes_sub(l::Transmission, mode_type::TransmissionMode)
modes_sub(ℒᵗʳᵃⁿˢ::Vector{<:Transmission}, mode_type::TransmissionMode)
```

指定された `mode_type` のすべての [`TransmissionMode`](@ref)s を含む配列を返します。これは [`Transmission`](@ref) 回廊 `l` または伝送回廊のベクトル `ℒᵗʳᵃⁿˢ` に対して行われます。
