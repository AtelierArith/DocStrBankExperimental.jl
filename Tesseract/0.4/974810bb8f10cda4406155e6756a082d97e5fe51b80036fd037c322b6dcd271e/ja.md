```
tess_unlv(
    inst::TessInst
)::Union{String, Nothing}
```

UNLV形式のUTF-8で拒否および疑わしいコードを抽出します。エラーが発生した場合は`nothing`が返されます。

**引数:**

| T   | 名前   | デフォルト | 説明                |
|:--- |:---- |:----- |:----------------- |
| R   | inst |       | 呼び出すテッサラクトインスタンス。 |

**詳細:**

このメソッドは、画像に対してまだ呼び出されていない場合、`tess_recognize()`を呼び出します。

このメソッドは、他の何よりもOCR結果をテストするために使用されます。元のLatin1エンコーディングを使用したい場合は、[`tess_unlv_latin1`](@ref)メソッドを使用してください。

**例:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

unlv = tess_unlv(instance)

for line in split(unlv, '\n'; keepempty = false)[1:5]
    println(line)
end

# 出力

No one would have believed in the last years of the
the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man's and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
```

参照: [`tess_lstm_box`](@ref), [`tess_word_box`](@ref), [`tess_text_box`](@ref),           [`tess_unlv_latin1`](@ref)
