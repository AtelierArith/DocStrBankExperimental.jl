```
BLS(t, y, [yerr];
    duration, periods=autoperiod(t, duration, kwargs...), 
    objective=:likelihood, oversample=10, kwargs...)
```

ボックス最小二乗周期図を計算します。

# パラメータ

  * `t` - 各観測の時間。単位は重要ではありませんが、すべての時間的パラメータ（例：`duration`）に対して一貫性が必要です。`Unitful.jl`の単位は、変換することなくシームレスに機能します。
  * `y` - 各観測のフラックス値
  * `yerr`、オプション - 各観測の不確実性。提供されない場合は、デフォルトで1になります。
  * `duration` - 考慮すべき期間または期間。`t`と同じ単位
  * `periods`、オプション - BLSパワーを計算するための期間グリッド。提供されない場合は、[`autoperiod`](@ref)が呼び出され、追加のキーワード引数（`minimum_period`など）が使用されます。
  * `objective`、オプション - 尤度を最大化するか（`:likelihood`、デフォルト）信号対雑音比（`:snr`）のいずれかを選択します。
  * `oversample`、オプション - 使用するべき各期間あたりのビンの数。`oversample`の値が大きいほど、より細かいグリッドになります。

返される値は、便利な型[`BoxLeastSquares.BLSPeriodogram`](@ref)にラップされます。
