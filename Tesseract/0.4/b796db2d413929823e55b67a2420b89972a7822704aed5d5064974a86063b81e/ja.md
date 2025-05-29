```
tess_read_debug_config(
    inst::TessInst,
    filename::AbstractString
)::Nothing
```

ファイルからデバッグ設定をTesseractインスタンスに読み込みます。

**引数:**

| T   | 名前       | デフォルト | 説明                      |
|:--- |:-------- |:----- |:----------------------- |
| R   | inst     |       | 設定を読み込むTesseractインスタンス。 |
| R   | filename |       | 設定を読み込むファイルの名前。         |

**詳細:**

デバッグ設定のみが読み込まれ、他の設定は無視されます。

参照: [`tess_read_config`](@ref)
