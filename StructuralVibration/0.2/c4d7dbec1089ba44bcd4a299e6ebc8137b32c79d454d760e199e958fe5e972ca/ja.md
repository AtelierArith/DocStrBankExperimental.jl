```
FFTParameters
```

FFT分析のための時間および周波数パラメータを格納する構造体

**コンストラクタ**

  * `fs::Real`: 信号のサンプリングレート
  * `bs::Real`: 信号のブロックサイズ
  * `pow2::Bool`: 次の2の累乗を見つけるためのフラグ

**フィールド**

  * `t::AbstractRange`: 時間ベクトル
  * `dt::Float64`: 時間ステップ
  * `tspan::Tuple{Float64, Float64}`: 時間範囲
  * `freq::AbstractRange`: 周波数ベクトル
  * `df::Float64`: 周波数分解能
  * `freq_span::Tuple{Float64, Float64}`: 周波数範囲
  * `fs::Int`: サンプリングレート
  * `bs::Int`: ブロックサイズ
