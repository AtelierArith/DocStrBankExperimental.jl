再構成されたトラッカーパルス

  * 著者: Wenxing Fang, IHEP

# フィールド

  * `cellID::UInt64`: セルID。
  * `time::Float32`: 時間 [ns]。
  * `charge::Float32`: 電荷 [fC]。
  * `quality::Int16`: 品質。
  * `covMatrix::SVector{3,Float32}`: 電荷(c)と時間(t)の測定値の下三角共分散行列。

# 関係

  * `timeSeries::TimeSeries`: オプションとして、パルスを作成するために使用されたtimeSeriesをパルスと一緒に保存できます。
