```
tess_unlv_latin1(
    inst::TessInst
)::Union{String, Nothing}
```

UNLV形式のLatin-1で、拒否および疑わしいコードを含むテキストを抽出します。エラーが発生した場合は`nothing`が返されます。

**引数:**

| T   | 名前   | デフォルト | 説明                   |
|:--- |:---- |:----- |:-------------------- |
| R   | inst |       | 呼び出すTesseractインスタンス。 |

**詳細:**

このメソッドは、画像に対してまだ`tess_recognize()`が呼び出されていない場合に呼び出されます。

このメソッドは、他の何よりもOCR結果をテストするために使用されます。このメソッドは、Latin1エンコーディングでOCRデータを返します。Juliaで文字列として使用したい場合は、[`tess_unlv`](@ref)メソッドを使用すると、UTF-8に変換されます。

**例:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

unlv = tess_unlv_latin1(instance)

# 出力

1470-element Vector{UInt8}:
 0x4e
 0x6f
 0x20
 0x6f
 0x6e
 0x65
 0x20
 0x77
 0x6f
 0x75
    ⋮
 0x6f
 0x6e
 0x6d
 0x65
 0x6e
 0x74
 0x2e
 0x0a
 0x0a
```

関連情報: [`tess_lstm_box`](@ref), [`tess_word_box`](@ref), [`tess_text_box`](@ref),           [`tess_unlv`](@ref) ```
