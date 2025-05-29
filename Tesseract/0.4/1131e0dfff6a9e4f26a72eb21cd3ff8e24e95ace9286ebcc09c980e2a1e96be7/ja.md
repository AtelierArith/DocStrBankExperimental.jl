```
tess_read_config(
    inst::TessInst,
    filename::AbstractString
)::Nothing
```

ファイルから設定を読み込み、Tesseract インスタンスにロードします。

**引数:**

| T   | 名前       | デフォルト | 説明                         |
|:--- |:-------- |:----- |:-------------------------- |
| R   | inst     |       | 設定をロードする Tesseract インスタンス。 |
| R   | filename |       | 設定をロードするファイルの名前。           |

関連情報: [`tess_read_debug_config`](@ref)
