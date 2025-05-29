```
FredQD(path::String)
FredQD(d::Date)
FredQD()
```

Fred QDデータをロードします。

## 引数

  * `path::String`: 手動でダウンロードしたFred QDのバージョンへのパス。
  * `d::Date`: ヴィンテージの日付。

## 詳細

  * 引数が提供されない場合、最も最近のFred QDのバージョンがダウンロードされます。
  * `d::Date`が提供されると、その日付に対応するFred QDのヴィンテージがダウンロードされます。
  * `path::String`が提供されると、指定された`path`のFred QDファイルがロードされます。

## 注意事項

  * Fred QDデータは、セントルイス連邦準備銀行のマイケル・W・マクラクンによって編纂されています。詳細については、公式ウェブサイト https://research.stlouisfed.org/econ/mccracken/fred-databases/ をご覧ください。
