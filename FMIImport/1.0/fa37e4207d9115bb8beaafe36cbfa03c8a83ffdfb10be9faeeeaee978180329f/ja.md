```
fmi2GetEventIndicators(c::FMU2Component)
```

FMUのイベントインジケーターを返します

# 引数

  * `c::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンスを表す可変構造体。

# 戻り値

  * `eventIndicators::Array{fmi2Real}`: イベントインジケーターは、"fmi2Real"値の配列として表されるベクトルとして返されます。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

また[`fmi2GetEventIndicators!`](@ref)も参照してください。
