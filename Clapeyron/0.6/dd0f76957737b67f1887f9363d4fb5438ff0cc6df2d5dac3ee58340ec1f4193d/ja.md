```
DIPPR101Sat <: SaturationModel

DIPPR101Sat(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `A`: 単一パラメータ (`Float64`)
  * `B`: 単一パラメータ (`Float64`)
  * `C`: 単一パラメータ (`Float64`)
  * `D`: 単一パラメータ (`Float64`)
  * `E`: 単一パラメータ (`Float64`)
  * `Tmin`: 単一パラメータ (`Float64`)  - 最小温度範囲 `[K]`
  * `Tmax`: 単一パラメータ (`Float64`)  - 最大温度範囲 `[K]`

## モデルパラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `A`: 単一パラメータ (`Float64`)
  * `B`: 単一パラメータ (`Float64`)
  * `C`: 単一パラメータ (`Float64`)
  * `D`: 単一パラメータ (`Float64`)
  * `E`: 単一パラメータ (`Float64`)
  * `Tmin`: 単一パラメータ (`Float64`)  - 最小温度範囲 `[K]`
  * `Tmax`: 単一パラメータ (`Float64`)  - 最大温度範囲 `[K]`

## 説明

DIPPR 101の飽和圧力の方程式:

```
psat(T) = exp(A + B/T + C•log(T) + D•T^E)
```

## 参考文献

1. Design Institute for Physical Properties, 1996. DIPPR Project 801 DIPPR/AIChE
