```
tess_lstm_box(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{String, Nothing}
```

LSTMトレーニング用のUTF-8ボックスファイルを返します。エラーが発生した場合は'nothing'が返されます。

**引数:**

| T   | 名前   | デフォルト      | 説明                   |
|:--- |:---- |:---------- |:-------------------- |
| R   | inst |            | 呼び出すTesseractインスタンス。 |
| O   | page | `Int32(1)` | データを取得するページ。         |

**詳細:**

このメソッドは、画像に対してまだ呼び出されていない場合、`tess_recognize()`を呼び出します。

**例:**

```jldoctest; filter = r"(\s+)"
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

box = tess_lstm_box(instance)

for line in split(box, '\n'; keepempty = false)[1:5]
    println(line)
end

# 出力

N 11 577 422 591 0
o 11 577 422 591 0
  11 577 422 591 0
o 11 577 422 591 0
n 11 577 422 591 0
```

参照: [`tess_unlv`](@ref), [`tess_word_box`](@ref), [`tess_text_box`](@ref)
