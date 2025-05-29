検出器の読み出しの生データ

  * 著者: F.Gaede, DESY

# フィールド

  * `cellID::UInt64`: 検出器特有のセルID。
  * `quality::Int32`: ヒットの品質フラグ。
  * `time::Float32`: ヒットの時間 [ns]。
  * `charge::Float32`: ヒットの統合電荷 [fC]。
  * `interval::Float32`: 各サンプリングの間隔 [ns]。
  * `adcCounts::PVector{Int32}`: iでの生データ (32ビット) ワード。

# メソッド

  * `setAdcCounts(object::RawTimeSeries, v::AbstractVector{Int32})`: `adcCounts` ベクターメンバーに値のセットを割り当てる。
