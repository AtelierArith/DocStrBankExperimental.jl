```
ekpsel(query, msglen=256, tablen=256, collen=256)
```

EKクエリのSELECT句を解析し、選択された各項目に関する詳細を返します。

### 引数

  * `query`: EKクエリ
  * `msglen`: 出力エラーメッセージ文字列の利用可能なスペース（デフォルト: 256）
  * `tablen`: `tabs`出力配列内の文字列の長さ（デフォルト: 256）
  * `collen`: `cols`出力配列内の文字列の長さ（デフォルト: 256）

### 出力

  * `xbegs`: SELECT句内の式の開始位置
  * `xends`: SELECT句内の式の終了位置
  * `xtypes`: 式のデータ型
  * `xclass`: 式のクラス
  * `tabs`: SELECT列を修飾するテーブルの名前
  * `cols`: クエリのSELECT句内の列の名前

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekpsel_c.html)
