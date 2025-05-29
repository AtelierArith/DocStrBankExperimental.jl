[Taper](@ref) オブジェクトを構築し、Slepian のマルチテーパリング *離散プロレート球面系列* を保持します。サンプリングレート `sr`、ウィンドウ長 `wl`、および Hz 単位の `bandwidth` 引数を指定します。EEG データの場合、1<=bandwidth<=2 が適切な選択です。

DSP パッケージおよびユニバーサル [Taper](@ref) コンストラクタで使用される '半帯域幅' パラメータ `α` は次のように設定されます。

```
    `α=(bandwidth/2)*wl/sr`.
```

最適な dpss の数は経験則的に次のように設定されます。

```
    `n=max(1, trunc(Int, 2*α)-trunc(Int, log(2*α)))`.
```

作成されたオブジェクトは、コンストラクタ [`spectra`](@ref)、[`crossSpectra`](@ref)、および [`coherence`](@ref) に引数として渡すことができます。

**参照**: [plot tapering windows](@ref)。

**例**:

```julia
using FourierAnalysis
sr, t, f, a = 128, 128, 10, 0.5
# 白色雑音に重ねられた正弦波を作成
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# データ行列を作成
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
# 帯域幅 1.5 で slepian マルチテーパリングを使用してスペクトルを計算
H=slepians(sr, t, 2)
S=spectra(X, sr, t; tapering=H)

using Plots
plot(H)
plot(S)
```
