# 関数呼び出し

`fourierSeriesStepReal(t, u, T, hMax)`

# 説明

データペア `t` と `u` に基づいてステップ関数 `u(t)` の実数フーリエ係数を以下の変数に従って計算します：

$$
\mathtt{a[k]} =
\frac{2}{\mathtt{T}} \int_{\mathtt{t[1]}}^{\mathtt{t[1]+T}}
\mathtt{u(t)} \cos(k\omega \mathtt{t}) \operatorname{d}\mathtt{t} \\
$$

$$
\mathtt{b[k]} =
\frac{2}{\mathtt{T}} \int_{\mathtt{t[1]}}^{\mathtt{t[1]+T}}
\mathtt{u(t)} \sin(k\omega \mathtt{t}) \operatorname{d}\mathtt{t}
$$

# 関数引数

`t` ステップが発生する時間ベクトルインスタンス

`u` フーリエ係数を決定するデータベクトル、すなわち `u[k]` は `t[k]` での右側のデータ値

`T` `u` の時間周期

`hMax` 決定される最大調和数

# 戻り値

`h` 調和数のベクトル、すなわち `h[1] = 0`（`u` の dc 値）、`h[hMax+1] = hMax`

`f` 調和数に関連する周波数ベクトル、すなわち `f = h / T`

`a` フーリエ級数のコサイン係数、ここで `a[1]` = `u` の dc 値

`b` フーリエ級数のサイン係数、ここで `b[1] = 0`

# 例

コードをコピーして貼り付け：

```julia
# 正方波のフーリエ近似
ts = [0; 1]                 # サンプリングされた時間データ
us = [-1; 1]                # 正方波のステップ関数
T = 2                       # 周期
hMax = 7                    # 最大調和数
(h, f, a, b) = fourierSeriesStepReal(ts, us, T, hMax)
(t, u) = fourierSeriesSynthesisReal(f, a, b)
using PyPlot
# (t, u) を右に周期的に1要素拡張
(tx, ux) = repeatPeriodically(ts, us, right=1)
step(tx, ux, where="post")  # 正方波関数
plot(t, u)                  # hMax = 7 までのフーリエ近似
```
