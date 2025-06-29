```
y_at_Τ = interpolate(data, Τ)
```

データフレームを補間して、$y(t)$を特徴づける時系列を含む、`:t`および`:output`列を持つ行のペア$(t_i, y(t_i))$を持つ。新しい時間`Τ`での関数$y(t)$を近似するためにデータを補間します。すなわち、$y(\Tau)$を知りたいのです。

[`simulate`](@ref)はそのようなデータフレームを返すため、`interpolate`は`data`の`:t`列に必ずしも存在しない特定の時間`Τ`での解を得るのに役立ちます。

# 引数

  * `data::DataFrame`: 時系列のデータフレームで、時間のための`:t`列と出力のための`:output`列を含む。
  * `Τ::Float64`: $y$を知りたい新しい時間。すなわち、$y(\Tau)$を知りたい。

# 戻り値

  * `y_at_Τ::Float64`: $t$が`Τ`に等しいときの$y$の値、$y(\Tau)$、線形補間に従って。

# 例

一次遅れ系の単位ステップ応答は、$t=\tau$のときに最終値の約$63\%$です。

```jldoctest
τ = 3.45
g = 1 / (τ * s + 1)           # FOシステム
U = 1 / s                     # 入力, U(s)
Y = g * U                     # 出力, Y(s)
data = simulate(g / s, 10.0)  # 出力, y(t)
y_at_τ = interpolate(data, τ) # ≈ y(τ)
# 出力
0.6320802858877126
```
