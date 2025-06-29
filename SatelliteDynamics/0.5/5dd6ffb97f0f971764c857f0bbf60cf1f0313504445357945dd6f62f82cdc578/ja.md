`Epoch`型は、時間の単一の瞬間を表します。これは、SatelliteDynamicsモジュール全体で使用されます。時間の瞬間を明確に定義し、さまざまな表現や異なる時間システムで時間を表示するための便利なインターフェースを提供することを目的としています。内部データメンバーも、時間の表現がナノ秒精度を維持し、数世代後でもナノ秒より大きな浮動小数点演算エラーが蓄積されないように選択されています。

`+`、`+=`、`-`、および `-=` 演算子をサポートしています。2つのEpochを差し引くことで、2つのEpoch間の時間差を返すことができます。`Real`数を加算する場合、それはEpochに加える秒数のオフセットとして解釈されます。

このクラスは、すべての算術演算子もサポートしています：`==`、`!=`、`<`、`<=`、`>`、`>=`

引数：

  * `year::Real` 年
  * `month::Real` 月
  * `day::Real` 日
  * `hour::Real` 時間（オプション）
  * `minute::Real` 分（オプション）
  * `second::Real` 秒（オプション）
  * `nanoseconds::Real` ナノ秒（オプション）
  * `tsys::String`: 初期化時のエポックの時間システム

Epochクラスは、文字列からも初期化できます。有効な文字列コンストラクタの例は次のとおりです：

```julia
epc = Epoch("2018-12-20")
epc = Epoch("2018-12-20T16:22:19.0Z")
epc = Epoch("2018-12-20T16:22:19.123Z")
epc = Epoch("2018-12-20T16:22:19.123456789Z")
epc = Epoch("2018-12-20T16:22:19Z")
epc = Epoch("20181220T162219Z")
epc = Epoch("2018-12-01 16:22:19 GPS")
epc = Epoch("2018-12-01 16:22:19.0 GPS")
epc = Epoch("2018-12-01 16:22:19.123 GPS")
epc = Epoch("2018-12-01 16:22:19.123456789 GPS")
```
