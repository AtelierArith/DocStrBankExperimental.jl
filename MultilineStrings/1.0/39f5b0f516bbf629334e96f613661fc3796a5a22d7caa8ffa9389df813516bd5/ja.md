```
multiline(str, indicators) -> AbstractString
```

提供されたスタイルと `indicators` 文字列にエンコードされたチョンプに従って、マルチライン文字列を操作します。

# 引数

  * `str::AbstractString`: 処理されるマルチライン文字列
  * `indicators::AbstractString`: スタイルとチョンプを表す簡潔な文字列。インジケーターは文字形式またはYAML形式のいずれかです：

      * `fs` / `>-`: 折りたたみとストリップ
      * `fc` / `>`: 折りたたみとクリップ
      * `fk` / `>+`: 折りたたみと保持
      * `ls` / `|-`: リテラルとストリップ
      * `lc` / `|`: リテラルとクリップ
      * `lk` / `|"`: リテラルと保持

詳細については [https://yaml-multiline.info](https://yaml-multiline.info) を参照してください。
