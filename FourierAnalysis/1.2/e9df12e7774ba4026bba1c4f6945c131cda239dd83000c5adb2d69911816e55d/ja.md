```julia
(1)
function mean(S :: FDobjects,
         frange :: fInterval)

(2)
function mean(𝐒 :: FDobjectsVector,
         frange :: fInterval;
        w :: Vector = [],
    check :: Bool   = true)

(3)
function mean(Y :: TFobjects,
         frange :: fInterval,
         trange :: tInterval)

(4)
function mean(𝒀 :: TFobjectsVector,
         frange :: fInterval,
         trange :: tInterval;
          w :: Vector = [],
      check :: Bool   = true)
```

周波数領域のデータを [FDobjects](@ref) から、時間-周波数領域のデータを [TFobjects](@ref) から取得し、その平均を返します。周波数と時間の領域は、`frange` と `trange` によって示され、これらはそれぞれ [fInterval](@ref) と [tInterval](@ref) の型です。

この関数の完全な入力/出力型は、以下の表に示されています。

| method | input object                   | output                               |
|:------:|:------------------------------ |:------------------------------------ |
| (1.1)  | [Spectra](@ref)                | `frange`¹ の平均スペクトルを保持するベクトル          |
| (1.2)  | [CrossSpectra](@ref)           | `frange`² の平均交差スペクトルを保持する複素行列        |
| (1.3)  | [Coherence](@ref)              | `frange`² の平均コヒーレンスを保持する実数行列         |
| (2.1)  | [SpectraVector](@ref)          | 型 (1.1) のベクトルのベクトル                   |
| (2.2)  | [CrossSpectraVector](@ref)     | 型 (1.2) の行列のベクトル                     |
| (2.3)  | [CoherenceVector](@ref)        | 型 (1.3) の行列のベクトル                     |
| (3.1)  | [TFAnalyticSignal](@ref)       | [`frange`, `trange`] の平均解析信号を保持する複素数 |
| (3.2)  | [TFAmplitude](@ref)            | [`frange`, `trange`] の平均振幅を保持する実数    |
| (3.3)  | [TFPhase](@ref)                | [`frange`, `trange`] の平均位相を保持する実数    |
| (4.1)  | [TFAnalyticSignalVector](@ref) | 型 (3.1) の数のベクトル                      |
| (4.2)  | [TFAmplitudeVector](@ref)      | 型 (3.2) の数のベクトル                      |
| (4.3)  | [TFPhaseVector](@ref)          | 型 (3.3) の数のベクトル                      |

凡例: ¹*ベクトルの各要素は、スペクトルが計算された時系列を参照します。* ² *オブジェクトの作成方法に応じて、行列はエルミートまたは下三角行列のいずれかになります。*

メソッド (2) と (4) では、次の *オプションのキーワード引数* を使用できます。

`w` は、非負の整数または実数の $k$-ベクトルであり、$k$ は入力 [FDobjectsVector](@ref) または [TFobjectsVector](@ref) に保持されるオブジェクトの数です。`w` は、入力オブジェクトから抽出された平均の重みのベクトルです。デフォルトでは、重みは割り当てられません。

`check` はブール値です。これが true (デフォルト) の場合、入力オブジェクトの非データフィールドがすべて同じであることが確認されます (たとえば、サンプリングレート、帯域幅など)。

**参照**: [`extract`](@ref)。

**例**:

```julia
using FourierAnalysis, Plots

# 単変量スペクトルオブジェクトの例 (1つの系列 -> 1つのスペクトル)
sr, t, f, a = 128, 256, 10, 1
# ホワイトノイズに重ねた正弦波を作成
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# スペクトルを計算
Σ=spectra(v, sr, t)
# 8Hz と 12Hz の間の平均スペクトル
s=mean(Σ, (8, 12))
# 8Hz と 12.5Hz の間の平均スペクトル
s=mean(Σ, (8, 12.5))

# 多変量スペクトルの例 (複数の系列 -> 複数のスペクトル)
Σ=spectra(hcat(v, v+randn(t*16)), sr, t)
# 8Hz と 12Hz の間の平均スペクトル
S=mean(Σ, (8, 12))
# 10Hz での平均スペクトル、すなわち 10Hz でのスペクトル
S=mean(Σ, 10)

# CrossSpectra オブジェクトの例 (Coherence オブジェクトにも同様)
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra(X, sr, t)
# 8Hz と 12Hz の間の平均交差スペクトル (エルミート行列)
S=mean(Σ, (8, 12))
Σ=crossSpectra(X, sr, t; tril=true)
# 8Hz と 12Hz の間の平均交差スペクトル (下三角行列)
S=mean(Σ, (8.0, 12.0)) # 周波数に整数と実数を受け入れる

# 複数の CrossSpectra オブジェクトの例
X2=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra([X, X2], sr, t) # これは CrossSpectraVector です
S=mean(Σ, (8, 12); w=[0.4, 0.6])
# これで S[1] は X の範囲 8-12Hz の平均交差スペクトルを保持し、
# S[2] は X2 の範囲 8-12Hz の平均交差スペクトルを保持します

# 時間-周波数オブジェクトの例
# (TFAnalyticSignal、TFAmplitude、TFPhase に対しても同様に機能します)
Y = TFanalyticsignal(v, sr, t)
# 周波数 8Hz と 12Hz、時間サンプル 1 から 64 までの平均解析信号。
as=mean(Σ, (8, 12), (1, 64))
# 周波数 8Hz と 12Hz の間の平均解析信号。
as=mean(Σ, (8, 12), :)
# 時間サンプル 1 から 64 までの平均解析信号。
as=mean(Σ, :, (1, 64))

# 複数の時間-周波数オブジェクトの例
Y = TFanalyticsignal([v, v+randn(t*16)], sr, t)
AS=mean(Y, (8, 12), (1, 64))
# これらの平均の TFobjects の平均を取得
m=mean(mean(Y, (8, 12), (1, 64)))
AS=mean(Y, (8), :)
AS=mean(Y, 8, 2)
```
