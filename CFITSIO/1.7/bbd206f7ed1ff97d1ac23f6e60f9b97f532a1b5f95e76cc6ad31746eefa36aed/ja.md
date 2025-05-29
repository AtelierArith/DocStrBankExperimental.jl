```
fits_resize_img(f::FITSFile, sz::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}})
```

画像を新しいサイズ `sz` にリサイズします。要素の型は保持され、次元の数は `length(sz)` に等しく設定されます。
