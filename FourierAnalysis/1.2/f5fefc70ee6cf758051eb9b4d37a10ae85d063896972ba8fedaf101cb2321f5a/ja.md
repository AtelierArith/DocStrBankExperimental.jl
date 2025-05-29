```julia
(1)
function extract(S :: FDobjects,
            frange :: fInterval)

(2)
function extract(𝐒 :: FDobjectsVector,
            frange :: fInterval;
        w :: Vector = [],
    check :: Bool   = true)

(3)
function extract(Y :: TFobjects,
            frange :: fInterval,
            trange :: tInterval)

(4)
function extract(𝒀 :: TFobjectsVector,
            frange :: fInterval,
            trange :: tInterval;
        w :: Vector = [],
    check :: Bool   = true)
```

**エイリアス**: `extr`

[FDobjects](@ref) から周波数領域のデータを抽出し、[TFobjects](@ref) から時間-周波数領域のデータを抽出します。周波数と時間の領域は、それぞれ [fInterval](@ref) と [tInterval](@ref) 型の `frange` と `trange` で示されます。

この関数の入力/出力タイプは、複数の周波数と複数のサンプルを持つ領域に対して、以下の表に示されています。

| メソッド  | 入力オブジェクト                       | 出力                                   |
|:-----:|:------------------------------ |:------------------------------------ |
| (1.1) | [Spectra](@ref)                | `frange` 内のスペクトルを列に配置した実数行列¹         |
| (1.2) | [CrossSpectra](@ref)           | `frange` 内のクロススペクトルを保持する複素行列のベクトル²   |
| (1.3) | [Coherence](@ref)              | `frange` 内のコヒーレンスを保持する実数行列のベクトル²     |
| (2.1) | [SpectraVector](@ref)          | タイプ (1.1) の行列のベクトル                   |
| (2.2) | [CrossSpectraVector](@ref)     | タイプ (1.2) のベクトルのベクトル                 |
| (2.3) | [CoherenceVector](@ref)        | タイプ (1.3) のベクトルのベクトル                 |
| (3.1) | [TFAnalyticSignal](@ref)       | [`frange`, `trange`] 内の解析信号を保持する複素行列 |
| (3.2) | [TFAmplitude](@ref)            | [`frange`, `trange`] 内の振幅を保持する実数行列   |
| (3.3) | [TFPhase](@ref)                | [`frange`, `trange`] 内の位相を保持する実数行列   |
| (4.1) | [TFAnalyticSignalVector](@ref) | タイプ (3.1) の行列のベクトル                   |
| (4.2) | [TFAmplitudeVector](@ref)      | タイプ (3.2) の行列のベクトル                   |
| (4.3) | [TFPhaseVector](@ref)          | タイプ (3.3) の行列のベクトル                   |

凡例: ¹ *各列は、スペクトルが計算された時系列を指します。* ² *オブジェクトの作成方法によって、行列はエルミートまたは下三角行列のいずれかになる場合があります。[CrossSpectra](@ref) および [Coherence](@ref) のドキュメントを参照してください。*

引数に応じて、出力の型は1つまたは2つの次元を失う場合があります。例えば、

  * [Spectra](@ref) オブジェクトが1つのスペクトルのみを保持している場合、(1.1) は列ベクトルを出力し、(2.1) は列ベクトルのベクトルを出力します。
  * `frange` が単一の周波数を指す場合、(1.1) は行ベクトルを出力し、(2.1) は行ベクトルのベクトルを出力します。
  * 上記の2つの条件が両方とも満たされる場合、(1.1) は実数を出力し、(2.1) はベクトルを出力します。
  * `frange` が単一の周波数を指す場合、(1.2)、(1.3) は行列を出力し、(2.2)、(2.3) は行列のベクトルを出力します。
  * `frange` が単一の周波数帯域を指す場合、(3.1)、(3.2)、(3.3) は行ベクトルを出力し、(4.1)、(4.2)、(4.3) は行ベクトルのベクトルを出力します。
  * `trange` が単一の時間サンプルを指す場合、(3.1)、(3.2)、(3.3) は列ベクトルを出力し、(4.1)、(4.2)、(4.3) は列ベクトルのベクトルを出力します。
  * 上記の2つの条件が両方とも満たされる場合、(3.1)、(3.2)、(3.3) は数値を出力し、(4.1)、(4.2)、(4.3) はベクトルを出力します。

メソッド (2) および (4) では、以下の*オプションのキーワード引数*を許可します：

`w` は、非負の整数または実数の $k$-ベクトルであり、$k$ は入力 [FDobjectsVector](@ref) または [TFobjectsVector](@ref) に保持されているオブジェクトの数です。`w` は、入力オブジェクトから抽出された領域の重みのベクトルです。デフォルトでは、重みは割り当てられません。

`check` はブール値です。これが true（デフォルト）である場合、入力オブジェクトの非データフィールドがすべて同じであることが確認されます（例えば、サンプリングレート、帯域幅など）。速度を向上させるために、false に設定します。

**関連情報**: [`mean`](@ref)。

**例**:

```julia
using FourierAnalysis

# 単変量スペクトルオブジェクトの例（1つの系列 -> 1つのスペクトル）
sr, t, f, a = 128, 256, 10, 1
# ホワイトノイズに重ねられた正弦波を作成
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# 単変量スペクトルを計算
Σ=spectra(v, sr, t)
# 8Hz と 12Hz の間のスペクトル
s=extract(Σ, (8, 12))
# 8Hz と 12.5Hz の間のスペクトル
s=extract(Σ, (8, 12.5))
# 10Hz のスペクトル
s=extract(Σ, 10) # または s=extract(S, (10, 10))
# これらの2つの式は同等です: s=extract(Σ, :), s=Σ.y

# 多変量スペクトルの例（複数の系列 -> 複数のスペクトル）
Σ=spectra(hcat(v, v+randn(t*16)), sr, t)
# 8Hz と 12Hz の間のスペクトル
S=extract(Σ, (8, 12))
# 10Hz のスペクトル
S=extract(Σ, 10)

# CrossSpectra オブジェクトの例（Coherence オブジェクトにも同様）
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra(X, sr, t)
# 8Hz と 12Hz の間のクロススペクトル（エルミート行列）
S=extract(Σ, (8, 12))
Σ=crossSpectra(X, sr, t; tril=true)
# 8Hz と 12Hz の間のクロススペクトル（下三角行列）
S=extract(Σ, (8, 12))

# 複数のクロススペクトルの例
X2=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra([X, X2], sr, t) # これは CrossSpectraVector です
S=extract(Σ, (8, 12); w=[0.4, 0.6])
# 現在 S[1] は X の範囲 8-12Hz のクロススペクトルを保持し、
# S[2] は X2 の範囲 8-12Hz のクロススペクトルを保持します

# 時間-周波数オブジェクトの例
# (TFAnalyticSignal、TFAmplitude、TFPhase に対しても同様に機能します)
Y = TFanalyticsignal(v, sr, t)
# 周波数 8Hz と 12Hz および時間サンプル 1 から 64 までの解析信号。
AS=extract(Y, (8, 12), (1, 64))

# 周波数 8Hz と 12Hz のすべての解析信号。
AS=extract(Y, (8.0, 12), :) # 周波数に整数と実数を受け入れます

# 時間サンプル 1 から 64 までのすべての解析信号。
AS=extract(Y, :, (1, 64))

# 複数の時間-周波数オブジェクトの例
# (出力の型がどのように変化するかに注意)
Y = TFanalyticsignal([v, v+randn(t*16)], sr, t)
AS=extract(Y, (8, 12), (1, 64))
AS=extract(Y, (8), :)
AS=extract(Y, 8, 2)
```
