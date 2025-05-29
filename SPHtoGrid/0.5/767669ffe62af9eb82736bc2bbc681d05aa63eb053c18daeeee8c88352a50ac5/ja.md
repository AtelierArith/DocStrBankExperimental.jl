```
write_fits_image(filename::String, image::Array{<:Real}, 
                        par::mappingParameters; 
                        units::String="[i.u.]",
                        snap::Integer=0)
```

マッピングされた画像をFITSファイルに書き込み、重要なマッピングパラメータをヘッダーに保存します。
