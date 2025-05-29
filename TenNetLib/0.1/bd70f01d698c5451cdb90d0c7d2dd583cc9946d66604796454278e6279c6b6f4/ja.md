```
mutable struct SweepData
    sweepcount::Int
    maxchi::Vector{Int}
    energy::Vector{Float64}
    entropy::Vector{Float64}
    maxtruncerr::Vector{Float64}
    lasteigs::Vector{Vector{Float64}}
end
```

各（完全）スイープ後の履歴データを保持します。収束チェックなどに必要です。

  * `sweepcount::Int`: 実行された完全スイープの数。
  * `maxchi::Vector{Int}`: 各スイープ後の最大MPSボンド/リンク次元。
  * `energy::Vector{Float64}`: 各スイープ後のエネルギー。
  * `entropy::Vector{Float64}`: 各スイープ後の中間チェーンエントロピー。
  * `maxtrucerr::Vector{Float64}`: 各スイープ後の最大切断誤差。
  * `lasteigs::Vector{Vector{Float64}}`: 前の半スイープ後の各ボンドでの固有値のスペクトル。

#### デフォルトコンストラクタ:

  * `SweepData()`: 空の `SweepData` オブジェクトを初期化します。
