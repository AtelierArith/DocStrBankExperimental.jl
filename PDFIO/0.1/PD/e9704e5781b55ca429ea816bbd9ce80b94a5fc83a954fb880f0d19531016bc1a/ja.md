```
    pdPageGetMediaBox(page::PDPage) -> CDRect{Float32}
    pdPageGetCropBox(page::PDPage) -> CDRect{Float32}
```

```
ページに関連付けられたメディアボックスを返します。PDF 1.7仕様の14.11.2を参照してください。
```

通常、ページのための用紙の指定サイズです。クロップボックスが定義されていない場合、メディアボックスがデフォルトとなります。

# 例

```
julia> pdPageGetMediaBox(page)
Rect:[0.0 0.0 595.0 792.0]

julia> pdPageGetCropBox(page)
Rect:[0.0 0.0 595.0 792.0]
```
