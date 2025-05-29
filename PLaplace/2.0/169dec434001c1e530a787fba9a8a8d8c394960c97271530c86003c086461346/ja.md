```julia
write_error(
    file_name::String,
    data::PLaplace.PLaplaceData,
    error::Vector{Float64}
) -> Int64

```

指定されたファイルにヘッダーに対応する他の情報とともに、与えられたエラーを書き込みます。
