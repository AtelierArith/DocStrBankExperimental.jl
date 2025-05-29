```
SysLog{P}
```

フライトログで、配列構造体のようにアクセスできるベクトルの基本データを構造体として含んでいます。さらに、プロット用の派生/計算された値を含むデータの拡張ビューがあります。最後に、ログファイルの名前などのメタデータが含まれています。

  * `name::String`: フライトログの名前
  * `colmeta::Dict`
  * `syslog::StructArrays.StructArray{KiteUtils.SysState{P}} where P`: 構造体のベクトルのようにアクセスできるベクトルの構造体
