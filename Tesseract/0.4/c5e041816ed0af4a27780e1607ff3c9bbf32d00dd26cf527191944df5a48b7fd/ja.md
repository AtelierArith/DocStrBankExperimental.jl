```
tess_params_parsed(
        inst::TessInst
    )::Vector{TessParam}
```

すべてのTesseractパラメータをその値とともに[`TessParam`](@ref)オブジェクトの配列として取得します。

**引数:**

| T   | 名前   | デフォルト | 説明                         |
|:--- |:---- |:----- |:-------------------------- |
| R   | inst |       | パラメータを取得するTesseractインスタンス。 |

**詳細:**

`[`tess_params`](@ref)`の結果をコンピュータがより簡単に処理できるものに解析します。 各行のテキストは3つの値に分割されます：

  * パラメータの名前。
  * パラメータのデフォルト値（空の文字列である可能性があります）。
  * パラメータを説明するテキスト。

各値はタブで区切られ、説明は改行で終了します。

関連情報: [`TessParam`](@ref), [`tess_params`](@ref), [`tess_get_param`](@ref),           [`tess_set_param`](@ref)
