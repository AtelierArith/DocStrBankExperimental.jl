```
FredMD(path::String)
FredMD(d::Date)
FredMD()
```

Fred MDデータをロードします。

## 引数

  * `path::String`: 手動でダウンロードしたFred MDのバージョンへのパス。
  * `d::Date`: ヴィンテージの日付。

## 詳細

  * 引数が提供されていない場合、最も最近のFred MDのバージョンがダウンロードされます。
  * `d::Date`が提供されている場合、その日付に対応するFred MDのヴィンテージがダウンロードされます。
  * `path::String`が提供されている場合、指定された`path`のFred MDファイルがロードされます。

## 注意事項

  * Fred MDデータは、セントルイス連邦準備銀行のマイケル・W・マクラクンによって編纂されています。詳細については、公式ウェブサイト https://research.stlouisfed.org/econ/mccracken/fred-databases/ をご覧ください。
