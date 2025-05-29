# 関数呼び出し

`fourierSeriesSampledReal(t,u,T,hMax)`

# 説明

データペア `t` と `u` に基づいて、サンプリングされた関数 `u(t)` の実数フーリエ係数を計算します。

# 関数引数

`t` サンプル時間のベクトル

`u` フーリエ係数を決定するデータベクトル、すなわち `u[k]` は `t[k]` に関連付けられたサンプリングデータ値です。

`T` `u` の時間周期

`hMax` 決定する最大調和数

# 戻り値

`h` 調和数のベクトル、すなわち `h[1] = 0`（`u` の dc 値）、`h[hMax+1] = hMax`

`f` 調和数に関連付けられた周波数ベクトル、すなわち `f = h / T`

`a` フーリエ級数のコサイン係数、ここで `a[1]` = `u` の dc 値

`b` フーリエ級数のサイン係数、ここで `b[1] = 0`

# 例

コードをコピーして貼り付けます：

```julia
# 矩形波形のフーリエ近似
ts = [ 0; 1; 2; 3; 4; 5; 6; 7; 8; 9]    # サンプリングされた時間データ
us = [-1;-1;-1;-1;-1; 1; 1; 1; 1; 1]    # 矩形波のステップ関数
T = 10                      # 周期
hMax = 7                    # 最大調和数
(h, f, a, b) = fourierSeriesSampledReal(ts, us, hMax)
(t, u) = fourierSeriesSynthesisReal(f, a, b)
using PyPlot
# (t, u) を右に周期的に1要素拡張
(tx, ux) = repeatPeriodically(ts, us, right=1)
plot(tx, ux, marker="o")    # 矩形波関数
plot(t, u)                  # hMax = 7 までのフーリエ近似
```
