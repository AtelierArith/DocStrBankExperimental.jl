モデルの物理パラメータを初期化します。

```
PhysicalParameters(;
    ρ::Float64 = 900.0,
    g::Float64 = 9.81,
    ϵ::Float64 = 1e-3,
    η₀::F = 1.0, 
    maxA::Float64 = 8e-17,
    minA::Float64 = 8.5e-20,
    maxTlaw::Float64 = 1.0,
    minTlaw::Float64 = -25.0,
    noise_A_magnitude::Float64 = 5e-18
    )
```

# キーワード引数

```
- `ρ`: 氷の密度
- `g`: 重力定数
- `ϵ`: 小さな数
- `η₀`:  
- `maxA`: `A`の最大値（グレン係数）
- `minA`: `A`の最小値（グレン係数）
- `maxTlaw`: フェイク法でのシミュレーションに使用される温度の最大値
- `minTlaw`: フェイク法でのシミュレーションに使用される温度の最小値
- `noise_A_magnitude`: Aに加えられるノイズの大きさ
```
