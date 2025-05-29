```
    pdDocGetPageRange(doc::PDDoc, nums::AbstractRange{Int}) -> Vector{PDPage}
    pdDocGetPageRange(doc::PDDoc, label::AbstractString) -> Vector{PDPage}
```

ページ番号の範囲またはラベルを指定すると、それに関連付けられたページの配列が返されます。ページラベルの詳細な説明については、メソッド `pdDocHasPageLabels` を参照してください。

# 例

```
julia> pages = pdDocGetPageRange(doc, 1:4);

julia> typeof(pages)
Array{PDFIO.PD.PDPageImpl,1}

julia> length(pages)
4
```
