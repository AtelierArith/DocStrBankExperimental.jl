```julia
function bands(S :: Union{FDobjects, FDobjectsVector}
       bandwidth :: IntOrReal)
```

与えられた `bandwidth` で等間隔のバンドパス領域におけるスペクトル、クロススペクトル、またはコヒーレンス推定のバンドパス平均を返します。`bandwidth` は整数または実数として指定できます。バンドパス領域の定義の詳細については、[`bbands`](@ref) を参照してください。

バンドパス平均は、時間周波数オブジェクトにはサポートされていません。これらのオブジェクトには、コンストラクタの引数 `bandwidth` を使用して、同様の平均化がネイティブに利用可能です。

この関数の出力は次のようになります：

  * 単変量 [Spectra](@ref) オブジェクト（すなわち、1つのスペクトルのみを保持するもの）には、実数の列ベクトル、
  * 多変量 [Spectra](@ref) オブジェクトには、実数の行列、
  * [SpectraVector](@ref) オブジェクトには、上記のベクトル、
  * [CrossSpectra](@ref) および [Coherence](@ref) オブジェクトには、オブジェクトが構築された方法に応じて、エルミート行列または下三角行列のベクトル、
  * [CrossSpectraVector](@ref) および [CoherenceVector](@ref) オブジェクトには、上記のベクトル。

**参照**: [`bbands`](@ref)。

**例**:

```julia
using FourierAnalysis, Plots

# 単変量 Spectra オブジェクトの例（1つの系列 -> 1つのスペクトル）
sr, t, f, a = 128, 256, 10, 1
# ホワイトノイズに重ねた正弦波を作成
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# スペクトルを計算
Σ=spectra(v, sr, t)
# 2Hzバンドパス領域での平均スペクトル
b=bands(Σ, 2)
plot(b)

# 多変量スペクトルの例（複数の系列 -> 複数のスペクトル）
Σ=spectra(hcat(v, v+randn(t*16), v+randn(t*16) ), sr, t)
# すべての時系列に対する2Hzバンドパス領域での平均スペクトル
b=bands(Σ, 2)
plot(b)
# 時系列2と3のみの2Hzバンドパス領域での平均スペクトルをプロット
plot(bands(Σ, 2)[:, 2:3])

# CrossSpectra オブジェクトの例（Coherence オブジェクトにも同様）
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra(X, sr, t)
# 4Hzバンドパス領域での平均クロススペクトル
B=bands(Σ, 4)

# 複数の CrossSpectra オブジェクトの例
X2=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra([X, X2], sr, t) # これは CrossSpectraVector です
# すべてのクロススペクトルオブジェクトに対する4Hzバンドパス領域での平均クロススペクトル
B=bands(Σ, 4)
```
