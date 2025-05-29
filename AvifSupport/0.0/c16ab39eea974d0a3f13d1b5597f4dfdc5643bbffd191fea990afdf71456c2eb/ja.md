```
write_avif(dest_file::AbstractString, image::AbstractMatrix{<:Colorant}; kwargs...) -> Integer
write_avif(dest_file::AbstractString, image_arr::TVector; kwargs...) -> Integer
```

`Colorant`の行列または`Colorant`の行列の配列を`dest_file` Avif画像にエンコードするユーティリティ関数です。
