```
fits_insert_img(f::FITSFile, T::Type,
                naxes::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}}; prepend_primary::Bool = false)
```

現在のHDU（CHDU）の直後に新しい画像拡張を挿入するか、ファイルの先頭に新しいプライマリ配列を挿入します。

新しいプライマリ配列は、`prepend_primary`を`true`に設定して`fits_insert_img`を呼び出すことで、FITSファイルの先頭に挿入できます。この場合、既存のプライマリHDUは画像拡張に変換され、新しいプライマリ配列がCHDUになります。

挿入された配列のeltypeは`T`で、サイズは`naxes`です。

```
fits_insert_img(f::FITSFile, a::AbstractArray{<:Real}; prepend_primary::Bool = false)
```

要素型が`eltype(a)`で、サイズが`size(a)`の新しい画像HDUを挿入します。このHDUは配列`a`を格納することができます。フラグ`prepend_primary`を指定することで、FITSファイルの先頭に新しいプライマリ配列を挿入できます。
