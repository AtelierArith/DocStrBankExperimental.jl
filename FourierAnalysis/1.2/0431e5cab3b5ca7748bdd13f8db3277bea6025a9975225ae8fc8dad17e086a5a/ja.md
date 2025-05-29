```julia
(1)
function coherence(𝙎    :: CrossSpectra;
               allkinds :: Bool = false)

(2)
function coherence(𝓢    :: CrossSpectraVector;
               allkinds :: Bool = false,
               check    :: Bool = true)

(3)
function coherence(X  :: Matrix{T},
                   sr :: Int,
                   wl :: Int;
               tapering  :: Union{Taper, TaperKind} = harris4,
               planner   :: Planner                 = getplanner,
               slide     :: Int                     = 0,
               DC        :: Bool                    = false,
               nonlinear :: Bool                    = false,
               smoothing :: Smoother                = noSmoother,
               tril      :: Bool                    = false,
               allkinds  :: Bool                    = false,
               ⏩       :: Bool                    = true) where T<:Real

(4)
function coherence(𝐗 :: Vector{Matrix{T}},
              < same argument sr, ..., ⏩ of method (3) > where T<:Real


```

**alias**: coh

!!! note "export conflict"
    この識別子はDSPパッケージと競合する可能性があります。`FourierAnalysis.coherence`として呼び出してください。


(1)

[Coherence](@ref)オブジェクトを[CrossSpectra](@ref)オブジェクトから構築し、Welch法を使用してコヒーレンス推定を可能にします。データフィールド以外のすべてのフィールドはクロススペクトルオブジェクトからコピーされます。すなわち、`y`を除くすべてのフィールドがコピーされ、`y`にはこの関数によって計算されたコヒーレンス行列が保持されます。

`𝙎.tril`がtrueの場合、コヒーレンス行列の下三角部分のみが計算され、`y`の行列はLowerTriangular行列になります。そうでない場合、完全な行列が計算され、`y`はエルミート行列を保持します（[LinearAlgebra](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#Linear-Algebra-1）を参照）。

オプションのキーワード引数`allkinds`がtrueの場合、すべての5種類の[コヒーレンス](@ref)が返されます。この場合、出力はコヒーレンスオブジェクトの5タプルで、順序は次のとおりです。

  * *全体*コヒーレンス、
  * *実*コヒーレンス、
  * *瞬時*コヒーレンス、
  * *虚*コヒーレンス、
  * *遅延*コヒーレンス。

`allkinds`がfalse（デフォルト）の場合、*全体*（古典的）コヒーレンスのみが単一の`Coherence`オブジェクトとして返されます。

(2)

入力[CrossSpectraVector](@ref)オブジェクト`𝓢`から[CoherenceVector](@ref)オブジェクトを構築し、Welch法を使用してコヒーレンス推定を可能にします。このメソッドは、`𝓢`内のすべてのオブジェクトに対してメソッド(1)を呼び出します。

`allkinds`オプションのキーワードパラメータは、メソッド(1)と同じ意味を持ちます。このメソッドでは、引数がtrueとして渡されると、出力は`CoherenceVector`オブジェクトの5タプルになります。

オプションのキーワード引数`check`がtrue（デフォルト）の場合、`𝓢`内のすべての`CrossSpectra`オブジェクトが``.sr`, `.wl`, `.DC`, `.taper`, `.nonlinear`および`.smoothing`フィールドで同じ値を持つことが確認されます。これが満たされない場合、すべてのオブジェクトで同一でない最初のフィールドを指摘するエラーメッセージが表示され、`Nothing`が返されます。

(3)

次元$t$ x $n$の多変量時系列データ行列`X`が与えられたとき、ここで$t$はサンプル数（行）、$n$は時系列数（列）、サンプリングレート`sr`およびエポック長`wl`を用いて、`X`の二乗コヒーレンス行列を計算します。すなわち、Welch（スライディングウィンドウ）平均クロススペクトルから得られるすべてのフーリエ離散周波数でのコヒーレンス行列です。

**オプションのキーワード引数**:

`sr`、`wl`、`tapering`、`planner`および`slide`は[`spectra`](@ref)関数と同じ意味を持ちます。

`DC`、`nonlinear`、`smoothing`、`tril`および`⏩`は、クロススペクトルを推定するために適用される[`crossSpectra`](@ref)関数と同じ意味を持ちます。

`allkinds`オプションのキーワードパラメータは、メソッド(1)と同じ意味を持ちます。

(4)

実データ行列のベクトルから[CoherenceVector](@ref)オブジェクトを構築します。`𝐗`内のすべての$k$データ行列に対して、メソッド(3)に従ってWelch法を使用して推定されたクロススペクトル行列からコヒーレンス行列を計算します。

`𝐗`内の$k$行列は、同じ列数（すなわち、同じ時系列数）を持たなければなりませんが、任意の数の（少なくとも`wl`）行（サンプル）を持つことができます。他のすべての引数はメソッド(3)と同じ意味を持ち、以下の違いがあります。

`⏩`: trueの場合（デフォルト）、このメソッドは、$k$がJuliaに指示されたスレッド数の少なくとも2倍である場合、$k$データ行列全体でマルチスレッドモードで実行されます。そうでない場合、このメソッドはメソッド(3)に従って各コヒーレンス推定をシリーズ全体でマルチスレッドモードで実行しようとします。[Threads](@ref)を参照してください。

`Planner`が明示的に引数として渡されない場合、FFTWプランは一度計算され、すべてのコヒーレンス推定に適用されます。

**メソッド(1)および(3)に関する注意**:

`tril`がfalse（デフォルト）の場合、出力コヒーレンスオブジェクトは`Array{Hermitian,1}`型であり、これは[PosDefManifold](https://github.com/Marco-Congedo/PosDefManifold.jl)パッケージで使用される`ℍVector`型です。コヒーレンス推定は対称正定値であるため、PosDefManifoldの関数に引数としてすぐに使用できます。例えば、[測地線](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Geodesic-equations-1)上の行列移動、行列[距離](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.distance)など、または行列[平均](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Means-1)、[スペクトル埋め込み](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.spectralEmbedding)などを計算するために使用できます。

`tril`がtrueの場合、出力は`Array{LowerTriangular,1}`型であり、これはPosDefManifoldで使用される`𝕃Vector`型です。すなわち、コヒーレンスの下三角部分のみが計算され、時間とメモリを節約します。

**メソッド(2)および(4)に関する注意**:

`tril`がfalseの場合、出力は`Array{Array{Hermitian,1},1}`型であり、これは[PosDefManifold](https://github.com/Marco-Congedo/PosDefManifold.jl)で使用される`ℍVector₂`型です。

`tril`がtrueの場合、出力は`Array{Array{LowerTriangular,1},1}`型であり、これはPosDefManifoldで使用される`𝕃Vector₂`型です。

**参照**: [crossspectra.jl](@ref)、[Spectra](@ref)、[Coherence](@ref)。

**例**:

```julia
## メソッド(1)-(4)の共通コード

using FourierAnalysis, LinearAlgebra

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

# デフォルトのharris4テーパリングウィンドウを使用したクロススペクトル
S=crossSpectra(X, sr, wl)

# 古典的コヒーレンスのみ
C=FourierAnalysis.coherence(S)

# すべての5種類のコヒーレンス
Ctot, C2real, C3inst, C4imag, C5lag=FourierAnalysis.coherence(S, allkinds=true);
Ctot

# (2)

# 3つの多変量データ行列 8192x4を生成
X=[generateSomeData(sr, t) for i=1:3]

# デフォルトのharris4テーパリングウィンドウを使用したクロススペクトル
S=crossSpectra(X, sr, wl)

# 古典的コヒーレンスのみ
C=FourierAnalysis.coherence(S)

# すべての5種類のコヒーレンス
Ctot, C2real, C3inst, C4imag, C5lag=FourierAnalysis.coherence(S, allkinds=true);
Ctot

# (3)

X=generateSomeData(sr, t) # 多変量データ行列 8192x4

# デフォルトのharris4テーパリングウィンドウを使用したコヒーレンス
C=FourierAnalysis.coherence(X, sr, wl)

# 周波数5Hzでのコヒーレンス行列を確認
C.y[f2b(5, sr, wl)]

# ハンテーパリングウィンドウを使用したコヒーレンス
C=FourierAnalysis.coherence(X, sr, wl; tapering=hann)

# スレピアンのマルチテーパリングを使用
C=FourierAnalysis.coherence(X, sr, wl; tapering=slepians(sr, wl))

# 非線形コヒーレンス（位相ロッキング値）を計算
C=FourierAnalysis.coherence(X, sr, wl; tapering=slepians(sr, wl), nonlinear=true)

# コヒーレンス行列の下三角部分のみを計算
C=FourierAnalysis.coherence(X, sr, wl; tapering=slepians(sr, wl), tril=true)

# すべての5種類のコヒーレンスを計算
Ctot, Creal, Cinst, Cimag, Clag=FourierAnalysis.coherence(X, sr, wl;
    tapering=slepians(sr, wl), tril=true, allkinds=true);
Ctot

# コヒーレンスを事後にスムージング
C2=smooth(blackmanSmoother, C)

# すでにスムージングされたコヒーレンスを計算
C=FourierAnalysis.coherence(X, sr, wl;
            tapering=slepians(sr, wl), tril=true, smoothing=blackmanSmoother)

# 8Hz-12Hz範囲の平均コヒーレンス行列
M=mean(C, (8, 12)) # または M=mean(C, (8.0, 12.0))

# 8Hz-12Hz範囲のすべてのコヒーレンス行列を抽出
E=extract(C, (8, 12))

# 2Hzバンドパス領域で平均化されたコヒーレンス行列
B=bands(C, 2)

# (4)

# 3つの多変量データ行列 8192x4を生成
X=[generateSomeData(sr, t) for i=1:3]

# 以下の例はメソッド(3)と全く同じ構文を使用します。
# ただし、ここでの入力はデータ行列のベクトルであり、
# 単一のデータ行列ではないため、以下の例は
# メソッド(3)の例によって作成されたオブジェクトのベクトルを作成します。
# 例えば：

# デフォルトのharris4テーパリングウィンドウを使用したコヒーレンス
# これによりCoherenceVectorオブジェクトが作成されます
C=FourierAnalysis.coherence(X, sr, wl)

# 最初のCoherenceオブジェクトを確認
C[1]

# 最初のCoherenceオブジェクトの周波数5Hzでのコヒーレンス行列を確認
C[1].y[f2b(5, sr, wl)]

# ハンテーパリングウィンドウを使用したコヒーレンス
C=FourierAnalysis.coherence(X, sr, wl; tapering=hann)

# スレピアンのマルチテーパリングを使用
C=coherence(X, sr, wl; tapering=slepians(sr, wl))

# 非線形コヒーレンスを計算
C=FourierAnalysis.coherence(X, sr, wl; tapering=slepians(sr, wl), nonlinear=true)

# コヒーレンス行列の下三角部分のみを計算
C=FourierAnalysis.coherence(X, sr, wl; tapering=slepians(sr, wl), tril=true)

# すべての5種類のコヒーレンスを計算
Ctot, Creal, Cinst, Cimag, Clag=FourierAnalysis.coherence(X, sr, wl;
    tapering=slepians(sr, wl), tril=true, allkinds=true);
Ctot

# S内のすべてのコヒーレンスオブジェクトを事後にスムージング
C2=smooth(blackmanSmoother, C)

# すでにスムージングされたすべてを計算
C=FourierAnalysis.coherence(X, sr, wl; tapering=parzen, smoothing=blackmanSmoother)

# すべてのコヒーレンスオブジェクトの8Hz-12Hz範囲の平均コヒーレンス行列
M=mean(C, (8, 12)) # または M=mean(C, (8.0, 12.0))

# 上記のすべてのCoherenceオブジェクトにわたるグランド平均
meanM=mean(mean(C, (8, 12)))

# すべてのコヒーレンスオブジェクトの8Hz-12Hz範囲のすべてのコヒーレンス行列を抽出
E=extract(C, (8, 12))

# すべてのcoh.オブジェクトの8Hz-12Hz範囲のコヒーレンス行列のグランド平均
meanE=mean(extract(C, (8, 12)))

# すべてのcoh.オブジェクトの2Hzバンドパス領域で平均化されたコヒーレンス行列
B=bands(C, 2)

# FFTプランナーを事前に計算し、引数として渡す
# （これは関数が繰り返し呼び出される場合に興味深い）。
plan=Planner(plan_exhaustive, 10.0, wl, eltype(X[1])) # 10秒待つ
C=FourierAnalysis.coherence(X, sr, wl; planner=plan)

# これがどれだけ速くなるか？
using BenchmarkTools
@benchmark(FourierAnalysis.coherence(X, sr, wl))
@benchmark(FourierAnalysis.coherence(X, sr, wl; planner=plan))
...
...
```
