```julia
function sinusoidal(a :: IntOrReal,
                    f :: IntOrReal,
                   sr :: Int,
                    t :: Int,
                    θ :: IntOrReal = 0.;
                DClevel = 0.)
```

ピーク振幅 `a`、周波数 `f`、サンプリングレート `sr`、持続時間（サンプル数で） `t`、角度 `θ`（θ=0 はサイン波、θ=π/2 はコサイン波を生成）およびオプションのキーワード引数 `DC`（浮動小数点数）を使用して正弦波を生成します。DCレベルはデフォルトでゼロです。サイン波はゼロから始まるという慣習が採用されています。

**例**:

```julia
using FourierAnalysis, Plots

# ピーク振幅1、周波数12Hz、sr=64、位相=π/2の128サンプルの正弦波を作成してプロット
v=sinusoidal(1., 12, 64, 128, π/2)
plot(v)

# ゴーツェルアルゴリズムを使用して正弦波の振幅を推定
f, sr, t = 32, 128, 128
v=sinusoidal(3., f, sr, t, 0)
c=goertzel(v, f, sr, t) # cは0+3.0imと等しいはず
```
