```
ons(timeseries::String="L522", dataset::String="MM23")::TimeArray
```

ons() メソッドは、国家統計局 (ONS) から金融および経済の時系列データをダウンロードするためのラッパーです。

ons() メソッドは、ONS データベースからのデータセットと時系列コードに対応する 2 つの文字列引数を取ります。データベースを探索するには、https://www.ons.gov.uk/timeseriestool を使用できます。これは、追加情報がメタフィールドに含まれる TimeSeries.TimeArray データ構造でデータを返します。データには、月次値、四半期平均、年平均が含まれる場合があり、列名はそれぞれ monthly、quarterly、yearly です。タイムスタンプは期間の初日です。引数が提供されない場合、デフォルトのデータセットは住宅コストを含む消費者物価指数 (CPIH) であり、これは ONS のインフレの主要な指標です。

# 例

```julia
UK_RPI = ("CHAW","MM23")
UK_CPI = ("D7BT","MM23")
UK_CPIH = ("L522","MM23")
```

# 参考文献

https://www.ons.gov.uk/timeseriestool

# 参照

  * fred() はセントルイス連邦準備銀行の金融および経済データセットにアクセスします。
  * yahoo() は Yahoo Finance から株式の金融時系列をダウンロードするためのラッパーです。
