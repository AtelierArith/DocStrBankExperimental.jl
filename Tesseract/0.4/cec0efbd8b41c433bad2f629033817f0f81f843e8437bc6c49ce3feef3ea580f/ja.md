```
tess_params(
    inst::TessInst,
    filename::AbstractString
)::Bool
```

指定されたファイルにすべてのパラメータとその値、およびヘルプテキストを出力します。エラーが発生した場合はfalseを返します。

**引数:**

| T   | 名前       | デフォルト | 説明                            |
|:--- |:-------- |:----- |:----------------------------- |
| R   | inst     |       | パラメータを取得するためのTesseractインスタンス。 |
| R   | filename |       | 書き込むファイル名。                    |

**詳細:**

このメソッドは、各パラメータの名前、値、および変数に関する説明テキストを出力します。各変数はそれぞれの行にあり、各値の間にはタブ文字が区切りとして使用されます。

関連情報: [`tess_params_parsed`](@ref), [`tess_get_param`](@ref), [`tess_set_param`](@ref)
