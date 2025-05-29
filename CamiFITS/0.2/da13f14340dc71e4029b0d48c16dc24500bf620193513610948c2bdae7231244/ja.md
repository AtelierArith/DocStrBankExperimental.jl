```
FITS_HDU
```

単一の「ヘッダーとデータユニット」（HDU）を保持するオブジェクトです。

フィールドは次のとおりです。

  * `.hduindex:`:  識別子（ファイルには複数のHDUが含まれる場合があります） (`:Int`)
  * `.header`:  ヘッダーオブジェクト (`::FITS_header`)
  * `.dataobject`:  データオブジェクト (`::FITS_dataobject`)

注：空のデータブロック（`.dataobject = nothing`）は標準に準拠しています。
