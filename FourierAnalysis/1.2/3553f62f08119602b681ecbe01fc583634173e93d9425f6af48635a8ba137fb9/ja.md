```julia
(1)
function crossSpectra( X    :: Matrix{T},
                       sr   :: Int,
                       wl   :: Int;
                  tapering  :: Union{Taper, TaperKind} = harris4,
                  planner   :: Planner                 = getplanner,
                  slide     :: Int                     = 0,
                  DC        :: Bool                    = false,
                  nonlinear :: Bool                    = false,
                  smoothing :: Smoother                = noSmoother,
                  tril      :: Bool                    = false,
                  ⏩       :: Bool                    = true) where T<:Real

(2)
function crossSpectra( 𝐗    :: Vector{Matrix{T}},
              < same argument sr, ..., ⏩ of method (1) > where T<:Real

```

(1)

実数の多変量データからWelch法を使用して[CrossSpectra](@ref)オブジェクトを構築します。

サンプリングレート`sr`とエポック長`wl`が与えられたとき、次元$t$x$n$の多変量データ行列`X`に対して、次元$n$x$n$の交差スペクトル行列を計算します。ここで、$t$はサンプル数（行数）であり、`n>1`は時系列の数（列数）です。

交差スペクトル行列は、作成されたオブジェクトの`.y`ベクトルフィールドに保持されます。`.y`の長さは、`wl`引数と`DC`オプションのキーワード引数に依存します（以下参照）。

**オプションのキーワード引数**:

`sr`、`wl`、`tapering`、`planner`、および`slide`は、[`spectra`](@ref)関数と同じ意味を持ちます。

`DC`: trueの場合、DCレベルの交差スペクトル行列が`y`の最初の位置に返されます（[CrossSpectra](@ref)オブジェクトのフィールドを参照）、そうでない場合（デフォルト）`y`の行列は最初の正の離散周波数、すなわち$sr/wl$ Hzから始まります。

`nonlinear`: trueの場合、DFT係数から振幅情報が排除され、すなわち、平均化される前にそのモジュラスで正規化されます。これにより、交差スペクトル行列（スペクトル）の対角要素がすべての周波数で1.0となる非線形推定が得られます（Congedo, 2018; Pascual-Marqui 2007）。デフォルトではfalseです。

`smoothing`: 周波数にわたって交差スペクトル行列にタイプ[Smoother](@ref)の平滑化関数を適用します。デフォルトでは平滑化は適用されません。

`tril`: false（デフォルト）の場合、全交差スペクトル行列が計算されます。そうでない場合は、その下三角部分のみが計算されます（以下参照）。

`⏩`: true（デフォルト）の場合、`X`の系列に対して、系列の数がJuliaに指示されたスレッドの数の少なくとも2倍である場合に、メソッドはマルチスレッドモードで実行されます。[Threads](@ref)を参照してください。

**戻り値**

`tril`がfalse（デフォルト）の場合、出力は`Array{Hermitian,1}`型であり、これは[PosDefManifold](https://github.com/Marco-Congedo/PosDefManifold.jl)パッケージで使用される`ℍVector`型です。交差スペクトル推定はエルミート正定値であるため、PosDefManifoldの関数への引数としてすぐに使用できます。例えば、[geodesics](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Geodesic-equations-1)上の行列移動、行列[距離](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.distance)など、また、行列[平均](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Means-1)、[スペクトル埋め込み](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.spectralEmbedding)などを計算するために全ベクトル出力を使用できます。

`tril`がtrueの場合、出力は`Array{LowerTriangular,1}`型であり、これはPosDefManifoldで使用される`𝕃Vector`型です。すなわち、交差スペクトルの下三角部分のみが計算され、時間とメモリを節約します。

(2)

実数の多変量データ行列のベクトルから[CrossSpectraVector](@ref)オブジェクトを構築します。`𝐗`内のすべての$k$データ行列に対して、Welch法に従って交差スペクトル行列を計算します。

`𝐗`内の$k$行列は、同じ列数（すなわち、同じ時系列の数）を持たなければなりませんが、任意の数の（少なくとも`wl`）行（サンプル）を持つことができます。他のすべての引数は、メソッド（1）と同じ意味を持ちますが、以下の違いがあります。

`⏩`: trueの場合（デフォルト）、メソッドは$k$データ行列に対してマルチスレッドモードで実行されます。$k$がJuliaに指示されたスレッドの数の少なくとも2倍でない場合、このメソッドはメソッド（1）に従って各交差スペクトル推定を系列に対してマルチスレッドモードで実行しようとします。[Threads](@ref)を参照してください。

`planner`が引数として明示的に渡されない場合、FFTWプランは一度計算され、すべての交差スペクトル推定に適用されます。

**戻り値**

`tril`がfalseの場合、出力は`Array{Array{Hermitian,1},1}`型であり、これは[PosDefManifold](https://github.com/Marco-Congedo/PosDefManifold.jl)で使用される`ℍVector₂`型です。

`tril`がtrueの場合、出力は`Array{Array{LowerTriangular,1},1}`型であり、これはPosDefManifoldで使用される`𝕃Vector₂`型です。

**参照**: [CrossSpectra](@ref)。

**関連**: [`spectra`](@ref), [`coherence`](@ref)。

**例**:

```julia
using FourierAnalysis, Plots, LinearAlgebra

function generateSomeData(sr::Int, t::Int; noise::Real=1.)
    # 長さtサンプルの4つの正弦波とsrサンプリングレート
    # ピーク振幅: 0.7, 0.6, 0.5, 0.4
    # 周波数:        5,   7,  13,  27
    # 位相:            0, π/4, π/2,   π
    v1=sinusoidal(0.7, 5,  sr, t, 0)
    v2=sinusoidal(0.6, 7,  sr, t, π/4)
    v3=sinusoidal(0.5, 13, sr, t, π/2)
    v4=sinusoidal(0.4, 27, sr, t, π)
    return hcat(v1, v2, v3, v4) + (randn(t, 4)*noise)
end

sr, wl, t = 128, 512, 8192

# (1)

X=generateSomeData(sr, t) # 多変量データ行列 8192x4

# デフォルトのharris4テーパリングウィンドウを使用した交差スペクトル
S=crossSpectra(X, sr, wl)

# 周波数5Hzでの交差スペクトル行列を確認
S.y[f2b(5, sr, wl)]

# この行列の対角部分のみをベクトルとして確認
diag(S.y[f2b(5, sr, wl)])

# hannテーパリングウィンドウを使用した交差スペクトル
S=crossSpectra(X, sr, wl; tapering=hann)

# Slepianのマルチテーパリングを使用
S=crossSpectra(X, sr, wl; tapering=slepians(sr, wl))

# 非線形交差スペクトルを計算
S=crossSpectra(X, sr, wl; tapering=slepians(sr, wl), nonlinear=true)

# 交差スペクトル行列の下三角部分のみを計算
S=crossSpectra(X, sr, wl; tapering=slepians(sr, wl), tril=true)

# 交差スペクトルを事後に平滑化
S2=smooth(blackmanSmoother, S)

# すでに平滑化された交差スペクトルを計算
S=crossSpectra(X, sr, wl;
               tapering=slepians(sr, wl), tril=true, smoothing=blackmanSmoother)

# 8Hz-12Hz範囲の平均交差スペクトル行列
M=mean(S, (8, 12)) # または M=mean(S, (8.0, 12.0))

# 8Hz-12Hz範囲のすべての交差スペクトル行列を抽出
E=extract(S, (8, 12))

# 2Hzバンドパス領域で平均化された交差スペクトル行列
B=bands(S, 2)

# CrossSpectraオブジェクトからスペクトルを取得
PowerSpectra=Spectra(S)

# CrossSpectraオブジェクトから振幅スペクトルを取得
AmpSpectra=Spectra(S, func=√)

# CrossSpectraオブジェクトからlog10スペクトルを取得
log10Spectra=Spectra(S, func=log10)

# スペクトルをプロット（recipes.jlを参照）
plot(AmpSpectra; fmax=32, xspace=4, ytitle="振幅")

# (2)
# 3つの多変量データ行列8192x4を生成
X=[generateSomeData(sr, t) for i=1:3]

# ここでの例は、前のメソッドとまったく同じ構文を使用します。
# ただし、ここでの入力はデータ行列のベクトルであり、
# 単一のデータ行列ではないため、以下の例は
# 上記の例で作成されたオブジェクトのベクトルを作成します。
# 例えば:

# デフォルトのharris4テーパリングウィンドウを使用した交差スペクトル
# これによりCrossSpectraVectorオブジェクトが作成されます
S=crossSpectra(X, sr, wl)

# 最初のCrossSpectraオブジェクトの周波数5Hzでの交差スペクトル行列を確認
S[1].y[f2b(5, sr, wl)]

# この行列の対角部分のみをベクトルとして確認
diag(S[1].y[f2b(5, sr, wl)])

# Hammingのテーパリングウィンドウを使用した交差スペクトル
S=crossSpectra(X, sr, wl; tapering=hamming)

# Slepianのマルチテーパリングを使用
S=crossSpectra(X, sr, wl; tapering=slepians(sr, wl))

# 非線形交差スペクトルを計算
S=crossSpectra(X, sr, wl; tapering=slepians(sr, wl), nonlinear=true)

# 交差スペクトル行列の下三角部分のみを計算
S=crossSpectra(X, sr, wl; tapering=slepians(sr, wl), tril=true)

# S内のすべてのCrossSpectraオブジェクトを事後に平滑化
S2=smooth(blackmanSmoother, S)

# すでに平滑化されたすべてを計算
S=crossSpectra(X, sr, wl; tapering=parzen, smoothing=blackmanSmoother)

# すべてのCrossSpectra（CS）オブジェクトの8Hz-12Hz範囲の平均交差スペクトル行列
M=mean(S, (8, 12)) # または M=mean(S, (8.0, 12.0))

# 上記のすべてのCSオブジェクトにわたるグランド平均
meanM=mean(mean(S, (8, 12)))

# すべてのCSオブジェクトの8Hz-12Hz範囲のすべての交差スペクトル行列を抽出
E=extract(S, (8, 12))

# すべてのCSオブジェクトの8Hz-12Hz範囲の交差スペクトル行列のグランド平均
meanE=mean(extract(S, (8, 12)))

# すべてのCSオブジェクトの2Hzバンドパス領域で平均化された交差スペクトル行列
B=bands(S, 2)

# CrossSpectraオブジェクトからスペクトルを取得してプロット
plot(Spectra(S[1]); fmax=32, xspace=4)

# FFTプランナーを事前に計算し、引数として渡す
# （この関数が繰り返し呼び出される場合に興味深い）。
plan=Planner(plan_exhaustive, 10.0, wl, eltype(X[1])) # 10秒待つ
S=crossSpectra(X, sr, wl; planner=plan)

# これがどれだけ速くなるか？
using BenchmarkTools
@benchmark(crossSpectra(X, sr, wl))
@benchmark(crossSpectra(X, sr, wl; planner=plan))
...
...


```
