```
mutable struct SweepDataTTN
    sweepcount::Int
    maxchi::Vector{Int}
    energy::Vector{Float64}
end
```

TTNの各（フル）スイープ後の履歴データを保持します。収束チェックなどに必要です。

  * `sweepcount::Int`: 実行されたフルスイープの数。
  * `maxchi::Vector{Int}`: 各スイープ後の最大MPSボンド/リンク次元。
  * `energy::Vector{Float64}`: 各スイープ後のエネルギー。

#### デフォルトコンストラクタ:

  * `SweepDataTTN()`: 空の`SweepData`オブジェクトを初期化します。
