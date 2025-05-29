```
fmi3GetEventIndicators(c::FMU3Instance)
```

FMUのイベントインジケーターを返します

# 引数

  * `c::FMU3Instance`: FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。

# 戻り値

  * `eventIndicators::Array{fmi3Float64}`: イベントインジケーターは、"fmi3Float64"値の配列として表されるベクトルとして返されます。

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 3.2.1. 状態: 連続時間モード

他にも[`fmi3GetEventIndicators`](@ref)を参照してください。
