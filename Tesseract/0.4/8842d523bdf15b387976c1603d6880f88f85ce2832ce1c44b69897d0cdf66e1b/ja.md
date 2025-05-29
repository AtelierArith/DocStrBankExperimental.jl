```
tess_text_box(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{String, Nothing}
```

ページ上の識別された文字のボックスを取得します。エラーが発生した場合は'nothing'が返されます。

**引数:**

| T   | 名前   | デフォルト      | 説明                |
|:--- |:---- |:---------- |:----------------- |
| R   | inst |            | 呼び出すテッサラクトインスタンス。 |
| O   | page | `Int32(1)` | データを取得するページ。      |

**詳細:**

このメソッドは、画像に対してまだ呼び出されていない場合、`tess_recognize()`を呼び出します。結果は主にトレーニング目的で役立ちます。

結果の各行は、6つの値で識別された文字を示します：

  * 認識された文字。
  * 左端からのピクセルで測定された文字の左端。
  * 画像の下からのピクセルで測定された文字の下端。
  * 左端からのピクセルで測定された文字の右端。
  * 画像の下からのピクセルで測定された文字の上端。
  * 認識に使用されたページ（0ベース）。

**例:**

```jldoctest"
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

box = tess_text_box(instance)

for line in split(box, '\n'; keepempty = false)[1:5]
  println(line)
end

# 出力

N 11 580 17 591 0
o 19 580 25 588 0
o 35 580 41 588 0
n 43 580 49 588 0
e 51 580 57 588 0
```

参照: [`tess_unlv`](@ref), [`tess_lstm_box`](@ref), [`tess_word_box`](@ref)
