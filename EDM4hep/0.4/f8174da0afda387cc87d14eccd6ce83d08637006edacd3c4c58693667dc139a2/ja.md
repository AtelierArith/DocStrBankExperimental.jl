キャリブレーション済み検出器データ

  * 著者: Wenxing Fang, IHEP

# フィールド

  * `cellID::UInt64`: セルID。
  * `time::Float32`: 開始時間 [ns]。
  * `interval::Float32`: 各サンプリングの間隔 [ns]。
  * `amplitude::PVector{Float32}`: キャリブレーション済み検出器データ。

# メソッド

  * `setAmplitude(object::TimeSeries, v::AbstractVector{Float32})`: `amplitude` ベクターメンバーに値のセットを割り当てる。
