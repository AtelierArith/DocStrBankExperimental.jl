```
modes_sub(ℳ::Vector{<:TransmissionMode}, str::String)
modes_sub(ℳ::Vector{<:TransmissionMode}, str_arr::Array{String})
```

名前に文字列 `str` または文字列配列 `str_arr` のいずれかの値を含むすべての [`TransmissionMode`](@ref)s を含む配列を返します。
