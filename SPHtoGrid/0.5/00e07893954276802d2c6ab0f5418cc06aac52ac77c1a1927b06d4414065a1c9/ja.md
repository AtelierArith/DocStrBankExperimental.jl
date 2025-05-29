```
write_fits_image(filename::String, image::Array{<:Real};
                units::String = "[i.u.]",
                snap::Integer = 0)
```

マッピングされた全天画像をFITSファイルに書き込み、ヘッダーに単位とスナップショット番号を保存します。
