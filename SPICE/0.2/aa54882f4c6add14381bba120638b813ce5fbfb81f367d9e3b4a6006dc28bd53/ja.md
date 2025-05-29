```
matchi(string, templ, wstr, wchar)
```

ワイルドカードを含むテンプレートによって文字列が一致するかどうかを判断します。パターン比較は大文字と小文字を区別しません。

### 引数

  * `string`: テストする文字列
  * `templ`: 文字列に対してテストするテンプレート（ワイルドカード付き）
  * `wstr`: ワイルド文字列トークン
  * `wchr`: ワイルドキャラクタートークン

### 出力

文字列が一致する場合は `true` を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/matchi_c.html)

```
