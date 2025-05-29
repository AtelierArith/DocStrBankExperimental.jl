```julia
struct PersonParameter{U<:Real}
```

単一の推定された人のパラメータを保持するコンテナ。

## フィールド

  * `value`: 推定された能力値
  * `se`: 推定された標準誤差

## メソッド

  * [`value`](@ref): 人のパラメータ推定を抽出する
  * [`se`](@ref): 推定の標準誤差を抽出する
