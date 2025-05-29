fred(data::String="CPIAUCNS")::TimeArray

fred() メソッドは、セントルイス連邦準備銀行 (FRED) から金融および経済の時系列データをダウンロードするためのラッパーです。

fred() メソッドは、セントルイス連邦準備銀行 (FRED) データベースのシリーズコードに対応する文字列引数を取ります。データは TimeSeries.TimeArray データ構造で返されます。引数が提供されない場合、デフォルトのデータセットはすべての都市消費者の消費者物価指数: すべての項目 (CPIAUCNS) です。

# 例

```julia
DGS = fred("DGS10")
CPI = fred()
```

# 参考文献

https://research.stlouisfed.org/fred2

# 関連項目

  * yahoo() は、Yahoo Finance から株式の金融時系列をダウンロードするためのラッパーです。
  * ons()   は、国家統計局 (ONS) から金融および経済の時系列データをダウンロードするためのラッパーです。
