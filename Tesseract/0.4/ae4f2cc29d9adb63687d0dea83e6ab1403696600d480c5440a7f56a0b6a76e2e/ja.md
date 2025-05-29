```
tess_word_box(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{String, Nothing}
```

WordStr文字列を含むUTF8ボックスファイルを作成します。エラーが発生した場合は'nothing'が返されます。

**引数:**

| T   | 名前   | デフォルト      | 説明                   |
|:--- |:---- |:---------- |:-------------------- |
| R   | inst |            | 呼び出すTesseractインスタンス。 |
| O   | page | `Int32(1)` | データを取得するページ。         |

**詳細:**

このメソッドは、画像に対してまだ`tess_recognize()`が呼び出されていない場合に呼び出されます。結果はおそらくトレーニングに使用されます。

**例:**

```jldoctest; filter = r"(\s+)"
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

box = tess_word_box(instance)

for line in split(box, '\n'; keepempty = false)[1:5]
    println(line)
end

# 出力

WordStr 11 577 417 591 0 #誰もが信じなかった、最後の数年間の
    418 577 422 591 0
WordStr 11 557 457 571 0 #19世紀のこの世界が見守られていることを
    458 557 462 571 0
WordStr 10 537 457 551 0 #より大きな知性によって注意深く見守られていることを
```

参照: [`tess_unlv`](@ref), [`tess_lstm_box`](@ref), [`tess_text_box`](@ref)
