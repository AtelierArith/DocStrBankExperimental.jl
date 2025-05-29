```julia
(1)
function smooth(smoothing::Smoother,
                v::Vector{R}) where R<:RealOrComplex


(2)
function smooth(smoothing::Smoother,
                X::Matrix{R}; dims::Int=1) where R<:RealOrComplex

(2)
function smooth(smoother :: Smoother,
                S :: Union{FDobjects, FDobjectsVector})

(3)
function smooth(fsmoothing :: Smoother,
                tsmoothing :: Smoother,
                Y :: Union{TFobjects, TFobjectsVector})
```

タイプ [Smoother](@ref) のスムージング関数を適用します。

  * (1) 実数または複素数のベクトルに、
  * (2) 次元 `dims` に沿った実数または複素数の行列（デフォルト=1）に、
  * (3) [FDobjects](@ref) または [FDobjectsVector](@ref) 内のすべてのオブジェクトに、
  * (4) [TFobjects](@ref) または [TFobjectsVector](@ref) 内のすべてのオブジェクトに。

メソッド (1) と (2) は低レベルの計算のために提供されています。メソッド (3) と (4) はコンストラクタです。すべてのメソッドにおいて、出力は常に入力と同じタイプです。

メソッド (3) は周波数次元に沿ってスムージングを行います：

  * [Spectra](@ref) オブジェクトの場合、これは `.y` フィールド内の列ベクトルをスムージングすることに相当します。
  * [CrossSpectra](@ref) および [Coherence](@ref) オブジェクトの場合、これは `.y` フィールド内の隣接行列をスムージングすることに相当します。

メソッド (4) は周波数次元、時間次元、またはその両方に沿ってスムージングを行います。これは、オブジェクトの `.y` フィールド内の列ベクトル（周波数）および/または行ベクトル（時間）に沿ってスムージングを行うことに相当します。周波数次元にはスムージングを指定する必要があります（`fsmoothing`）、時間次元にもスムージングを指定する必要があります（`tsmoothing`）。どちらか一方は `noSmoother` であっても構いませんが、両方が `noSmoother` でない場合は、同じでなければなりません。周波数次元と時間次元の両方でスムージングが要求される場合、データは最初に時間次元でスムージングされ、その後に周波数次元でスムージングされます。[TFPhase](@ref) オブジェクトの場合、位相がアンラップされている場合にのみスムージングが許可されます。

この関数は、作成後に周波数領域および時間-周波数領域オブジェクトのスムージングを許可しますが、作成時にスムージングを要求することもできます。たとえば、[Spectra](@ref) のドキュメントを参照してください。

!!! note "Nota Bene"
    メソッド (1)、(2)、および (3) において、`Smoother` が `noSmoother` の場合、入力は変更されずに返されます。メソッド (4) では、`fsmoother` と `tsmoother` の両方が `noSmoother` の場合にこれが当てはまります。

    データ入力は、Hann または Hamming スムージングを適用するために、関係する次元で少なくとも 3 つの要素を保持する必要があります。また、Blackman スムージングを適用するためには、少なくとも 5 つの要素が必要です。


## 数学

$$
k
$$

要素から構成される系列 $x$ のスムージングは、要素 $i$ に対して次のように行われます。

$$
x_{i}=ax_{i-2}+bx_{i-1}+cx_{i}+bx_{i+1}+ax_{i+2}
$$

。

係数は次のとおりです。

| スムージングウィンドウ |  a   |  b   |  c   |
|:-----------:|:----:|:----:|:----:|
|    Hann     |  0   | 0.25 | 0.50 |
|   Hamming   |  0   | 0.23 | 0.54 |
|  Blackman   | 0.04 | 0.25 | 0.42 |

3点スムージングの場合、最初の点は次のようにスムージングされます。

$$
x_{1}=\frac{c}{b+c}x_{1} + \frac{b}{b+c}x_{2}
$$

最後の点（$k^{th}$）は次のようにスムージングされます。

$$
x_{k}=\frac{c}{b+c}x_{k} + \frac{b}{b+c}x_{k-1}
$$

。

5点スムージングの場合、最初の点は次のようにスムージングされます。

$$
x_{1}=\frac{c}{a+b+c}x_{1} + \frac{b}{a+b+c}x_{2} + \frac{a}{a+b+c}x_{3}
$$

、

2番目は次のようにスムージングされます。

$$
x_{2}=\frac{b}{a+2b+c}x_{1} + \frac{c}{a+2b+c}x_{2} + \frac{b}{a+2b+c}x_{3} + \frac{a}{a+2b+c}x_{4}
$$

、

最後から2番目は次のようにスムージングされます。

$$
x_{k-1}=\frac{a}{a+2b+c}x_{k-3} + \frac{b}{a+2b+c}x_{k-2} + \frac{c}{a+2b+c}x_{k-1} + \frac{b}{a+2b+c}x_{k}
$$

最後は次のようにスムージングされます。

$$
x_{k}=\frac{a}{a+b+c}x_{k-2} + \frac{b}{a+b+c}x_{k-1} + \frac{c}{a+b+c}x_{k}
$$

。

**参照**: [Smoother](@ref)

**例**:

```julia
using FourierAnalysis, Plots
sr, t, f, a = 128, 128, 10, 0.5
# 白色雑音に重ねられた正弦波を作成
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# 振幅スペクトルを計算
Σ=spectra(v, sr, t; func=√)
bar(Σ.y, labels="生の振幅スペクトル")

# スペクトルをスムージング
Σ2=smooth(blackmanSmoother, Σ)
bar!(Σ2.y, labels="スムージングされた振幅スペクトル")

# クロススペクトル（またはコヒーレンス）行列をスムージング
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
S=crossSpectra(X, sr, t) # またはコヒーレンス (X, sr, t)
# クロススペクトルをスムージング # またはコヒーレンス
S2=smooth(blackmanSmoother, S)

# 時間-周波数オブジェクトをスムージング
Y = TFanalyticsignal(v, sr, sr*4)
# 周波数をスムージング
Z=smooth(blackmanSmoother, noSmoother, Y)
# スムージングされた解析信号の振幅をプロット
heatmap(Z, amplitude)

# ASをスムージング: 周波数と時間の両方をスムージング
E=smooth(blackmanSmoother, blackmanSmoother, Y)
# スムージングされた解析信号の実部をプロット
heatmap(Z, real)
```
