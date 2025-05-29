```
apply_instrument_function(ν, α[, instrument_function=:rectangular, instrument_wing=10.0, instrument_resolution=0.1])
```

与えられた入力スペクトルに対して、インストゥルメント関数を適用します。

# 引数

  * `ν`: 波数ベクトル（注意：均等間隔が仮定されていますが、チェックはされていません！）
  * `α`: [`α`](@ref)を使用して計算された吸収係数
  * `instrument_function`（オプション）：以下のインストゥルメント関数のいずれかを示すシンボル
  * `instrument_wing`（オプション）：インストゥルメント関数を計算するための範囲の半幅 $cm^{-1}$
  * `instrument_resolution`（オプション）：インストゥルメント解像度の全幅 $cm^{-1}$

# 出力

インストゥルメント関数の影響を受けたスペクトルを持つ新しいベクトルを返します。

# インストゥルメント関数

以下のインストゥルメント関数 $I(x, Δ)$ がサポートされています。ここで `x` は関数を評価するための座標であり、その範囲は `instrument_wing` によって与えられます。`Δ` は解像度パラメータ `instrument_resolution` です。引数 `instrument_function` の値として記載されたシンボルを使用してください。

| シンボル           |                                                                         方程式                                                                          |                            説明 |
|:-------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------:| -----------------------------:|
| `:rectangular` |                   $\begin{cases} \frac{1}{Δ} & \lvert x \rvert \leq \frac{Δ}{2} \\ 0 & \lvert x \rvert > \frac{Δ}{2} \end{cases}$                    |                 矩形インストゥルメント関数 |
| `:triangular`  |             $\begin{cases} \frac{1}{Δ} (1 - \frac{\lvert x \rvert}{Δ}) & \lvert x \rvert \leq Δ \\ 0 & \lvert x \rvert > Δ \end{cases}$              |                三角形インストゥルメント関数 |
| `:gaussian`    |               $\frac{2}{Δ} \sqrt{\frac{\mathrm{ln}2}{\pi}} \mathrm{exp} \left (- \mathrm{ln}2 \left ( \frac{2x}{Δ}\right)^2 \right )$                |      ガウスインストゥルメント関数（例：広帯域ソース） |
| `:lorentzian`  |                                              $\frac{Δ}{2\pi} \frac{1}{x^2+\left(\frac{Δ}{2}\right)^2}$                                               | ローレンツインストゥルメント関数（例：単一周波数レーザー） |
| `:cosine`      | $\begin{cases} \frac{\pi}{4Δ} \cos \left ( \frac {\pi \lvert x \rvert}{2Δ} \right ) & \lvert x \rvert \leq Δ \\ 0 & \lvert x \rvert > Δ \end{cases}$ |               コサインインストゥルメント関数 |
| `:diffraction` |                                            $\frac{1}{Δ} \mathrm{sinc}^2 \left(  \frac{\pi x}{Δ} \right)$                                             |          回折（sinc型）インストゥルメント関数 |
| `:michelson`   |                                            $\frac{2}{Δ} \mathrm{sinc} \left(  \frac{2 \pi x}{Δ} \right)$                                             | マイケルソン干渉計型インストゥルメント関数（例：FTIR） |

```
