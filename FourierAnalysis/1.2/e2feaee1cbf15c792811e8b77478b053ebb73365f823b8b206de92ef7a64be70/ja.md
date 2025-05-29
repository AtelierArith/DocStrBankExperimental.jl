```julia
(1)
function spectra( X     :: Union{Vector{T}, Matrix{T}},
                  sr    :: Int,
                  wl    :: Int;
            tapering  :: Union{Taper, TaperKind} = harris4,
            planner   :: Planner                 = getplanner,
            slide     :: Int                     = 0,
            DC        :: Bool                    = false,
            func      :: Function                = identity, # equal to x->x
            smoothing :: Smoother                = noSmoother,
            ⏩       :: Bool                    = true) where T<:Real

(2)
function spectra( 𝐗   :: Vector{Matrix{T}},
            < same argument sr, ..., ⏩ of method (1) > where T<:Real
```

(1)

実数の単変量または多変量データから[Spectra](@ref)オブジェクトを構築します。サンプリングレート`sr`とエポック長`wl`が与えられた場合、次元$t$x$n$のベクトル（単変量）またはデータ行列（多変量）`X`のウェルチパワースペクトルを計算します。ここで、$t$はサンプル数（行数）、$n$は時系列の数（列数）です。

スペクトルは、作成されたオブジェクトの`.y`フィールドに保持されます。`X`がベクトルの場合、`.y`はベクトルであり、`X`が行列の場合、`.y`は`X`の列の信号のスペクトルを列に保持する行列です。スペクトルのサイズは、`DC`オプションのキーワード引数に依存します（下記参照）。これは、[Spectra](@ref)構造体のドキュメントに記載されています。

**オプションのキーワード引数**:

`tapering`: これは、[Taper](@ref)型のテーパリングオブジェクトまたは[TaperKind](@ref)型のテーパリングウィンドウの種類です。デフォルトでは、*harris4*テーパリングウィンドウが使用されます。テーパリングが不要な場合は、引数`tapering=rectangular`を渡します。この同じ構文は、すべての単純なテーパリングウィンドウを指定する最も便利な方法です。例：`tapering=hann`、`tapering=hamming`など。*離散プロレート球面系列（dpss）*のマルチテーパリングには、代わりに[`slepians`](@ref)コンストラクタを使用します。例：`tapering=slepians(sr, wl, 2)`のように引数を渡します。

`planner`: これは、FFTを計算するために使用される前方FFTWプランを保持する[`Planner`](@ref)オブジェクトのインスタンスです。デフォルトでは、このメソッドによってプランナーが計算されますが、事前に計算された場合はここに引数として渡すことができます。この関数が繰り返し呼び出される場合に興味深いです。

`slide`: これは、ウィンドウがスライドするサンプル数（ウェルチ法）です。デフォルトでは、サンプル数は50％のオーバーラップを許可するように選択されます。

`DC`: trueの場合、DCレベルのスペクトルが`y`の最初の行に返されます（[Spectra](@ref)オブジェクトのフィールドを参照）。そうでない場合（デフォルト）、`y`の行は最初の正の離散周波数から始まります。すなわち、$sr/wl$ Hzです。

`func`: これは、パワースペクトルを返す前に要素ごとに変換する関数です。無名関数を含みます。一般的な選択肢は次のとおりです：

  * `func=sqrt`は振幅スペクトルを返します。
  * `func=log`は対数パワースペクトルを返します。
  * `func=decibel`はデシベルでパワースペクトルを返します（[`decibel`](@ref)を参照）。

デフォルトでは、関数は適用されず、パワースペクトルが返されます。スムージングが要求されている場合（下記参照）、関数の後に適用されます。

`smoothing`: これは、隣接する周波数にわたってスペクトルに対して[スムーザー](@ref)型のスムージング関数を適用します。デフォルトでは、スムージングは適用されません。

`⏩`: trueの場合（デフォルト）、このメソッドは、`X`の系列がJuliaに指示されたスレッド数の少なくとも2倍である場合、系列にわたってマルチスレッドモードで実行されます。[Threads](@ref)を参照してください。

(2)

実数の単変量（ベクトル）または多変量データ（行列）のベクトルから[SpectraVector](@ref)オブジェクトを構築します。`𝐗`内のすべての$k$データベクトルまたはデータ行列に対して、メソッド（1）に従ってスペクトルを計算します。

`𝐗`がデータ行列を保持している場合、`𝐗`内の$k$行列は同じ列数（すなわち、同じ時系列の数）を持たなければなりませんが、任意の数の（少なくとも`wl`）行（サンプル）を持つことができます。他のすべての引数は、メソッド（1）と同じ意味を持ち、以下の違いがあります：

  * `⏩`: trueの場合（デフォルト）、このメソッドは、$k$がJuliaに指示されたスレッド数の少なくとも2倍である場合、$k$データ行列にわたってマルチスレッドモードで実行されます。そうでない場合、このメソッドは、メソッド（1）に従って各スペクトル推定を系列にわたってマルチスレッドモードで実行しようとします。[Threads](@ref)を参照してください。
  * `planner`が明示的に引数として渡されない場合、FFTWプランは一度計算され、すべてのスペクトル推定に適用されます。

**参照**: [Spectra](@ref)、[スペクトルをプロット](@ref)。

**関連**: [`crossSpectra`](@ref)、[`coherence`](@ref)、[goertzel.jl](@ref)。

**例**:

```julia
using FourierAnalysis

###################################################################

# (1)

# 正しい振幅スペクトルがすべての離散
# フーリエ周波数で返されることを確認します（矩形テーパーを使用）。
# サイン波はすべての周波数で振幅10で作成され、
# 最初の周波数で振幅10、次に周波数に沿って10単位ずつ増加します。
# NB tが偶数の場合、最後の周波数の正しい振幅は
# サイン波が特定の位相を持つ場合にのみ得られます。

sr, t, wl= 16, 32, 16
V=Matrix{Float64}(undef, t, wl)
for i=1:wl V[:, i]=sinusoidal(10*i, b2f(i, sr, t), sr, t, π/6) end

# FFTW.jlのみを使用
using FFTW
P=plan_rfft(V, 1)*(2/t);
Σ=abs.(P*V)
using Plots
bar(Σ[brange(t, DC=true), :], labels="")

# FourierAnalysis.jlを使用
Σ2=spectra(V, sr, t; tapering=rectangular, func=√, DC=true)
using Plots
bar(Σ2.y[brange(t, DC=true), :], labels="")

#############################################################################

### ウェルチ法によって得られた長い信号の振幅スペクトルを確認します
# 一つのサイン波は正確な離散フーリエ周波数にあり、もう一つはそうでない
# 矩形ウィンドウ
sr, t, f, a = 128, 128, 10, 0.5
v=sinusoidal(a, f, sr, t*16)+sinusoidal(a, f*3.5+0.5, sr, t*16)+randn(t*16);
Σ=spectra(v, sr, t; tapering=rectangular, func=√)
bar(Σ.y, labels="rectangular")

# harris4ウィンドウ（デフォルト）
Σ2=spectra(v, sr, t; func=√)
bar!(Σ2.y, labels="harris4")

# スムーズなスペクトル
Σ3=smooth(blackmanSmoother, Σ2)
bar!(Σ3.y, labels="smoothed")

#############################################################################

function generateSomeData(sr::Int, t::Int; noise::Real=1.)
    # 長さtサンプルの4つのサイン波とsrサンプリングレート
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
X=generateSomeData(sr, t)
# 多変量データ行列8192x4

# スペクトルを計算
S=spectra(X, sr, wl)

# 最初の系列のスペクトルを確認
S.y[:, 1]

# きれいなプロットを得るためのプロット属性を集める
using Plots.Measures
spectraArgs=(fmax = 32,
             left_margin = 2mm,
             bottom_margin = 2mm,
             xtickfont = font(11, "Times"),
             ytickfont = font(11, "Times"))
plot(S; spectraArgs...)
plot(S; xspace=2, spectraArgs...)

# カスタムの単純なテーパリングウィンドウを使用
S=spectra(X, sr, wl; tapering=riesz)

# スレピアンのマルチテーパリングを使用
S=spectra(X, sr, wl; tapering=slepians(sr, wl, 1.5))

# スムージングを使用して構築
S=spectra(X, sr, wl; tapering=slepians(sr, wl, 1.5), smoothing=hannSmoother)

# 代わりに振幅スペクトルを計算
S=spectra(X, sr, wl; tapering=slepians(sr, wl, 1.5), func=√)

# 振幅スペクトルをプロット
plot(S; ytitle="Amplitude", spectraArgs...)

# スペクトルを事後的にスムーズにする
S=smooth(blackmanSmoother, S)

# 範囲(8Hzから12Hz)のスペクトルを抽出
e=extract(S, (8, 12))

# シリーズ1と2の範囲(8Hzから12Hz)のスペクトルを抽出
e=extract(S, (8, 12))[:, 1:2]

# 10Hzでのみスペクトルを抽出（各系列1ビン）
e=extract(S, 10)

# 8Hz-12Hz範囲の平均スペクトル
bar(mean(S, (8.0, 12.0)))

# 8Hz-12Hz範囲の平均スペクトルの系列間平均
mean(mean(S, (8.0, 12.0)))

# 各系列のすべての周波数にわたる平均スペクトル
bar(mean(S, :))

# すべての系列の均等に間隔を空けた2Hzバンドパス領域の平均スペクトル
plot(bands(S, 2))

# シリーズ1と2の均等に間隔を空けた2Hzバンドパス領域の平均スペクトル
plot(bands(S, 2)[:, 1:2])

# (2)

# 8192x4の多変量データ行列を3つ生成
X=[generateSomeData(sr, t) for i=1:3]

# これでスペクトラ関数の呼び出しは3つのSpectraオブジェクトを生成します
S=spectra(X, sr, wl)
plot(S[1]; spectraArgs...)
plot(S[2]; spectraArgs...)
plot(S[3]; spectraArgs...)

# 多くのデータ行列のスペクトルを計算したい場合は、
# 高速なFFTWプランを使用して行うことをお勧めします（プランの計算に最大10秒待機）
plan=Planner(plan_exhaustive, 10.0, wl)
S=spectra(X, sr, wl; planner=plan)

# どれだけ速くなるのか？
using BenchmarkTools
@benchmark(spectra(X, sr, wl))
@benchmark(spectra(X, sr, wl; planner=plan))


# すべてのオブジェクトのすべての系列の範囲(8Hz-12Hz)の平均スペクトル
M=mean(S, (8, 12))

# 3つのオブジェクトのすべての系列に対する平均スペクトルをプロット
# Juliaの標準平均関数を使用
plot(mean(S[1].y[:, i] for i=1:size(S[1].y, 2)))
plot!(mean(S[2].y[:, i] for i=1:size(S[2].y, 2)))
plot!(mean(S[3].y[:, i] for i=1:size(S[3].y, 2)))

# 4Hz-32.5Hzの範囲のオブジェクト間の平均スペクトル
plot(mean(mean(S, (4, 32.5))))

# すべての系列とすべての被験者の範囲(8Hz-12Hz)のスペクトルを抽出
extract(S, (8, 12))

# 不正な範囲を入力すると、何も行われず、引数に何が問題かを説明する
# エラーがREPLに表示されます
extract(S, (0, 12))
mean(S, (1, 128))

# すべての系列とすべてのオブジェクトの4Hzバンドパス平均スペクトルを抽出
bands(S, 4)

# スペクトル計算にスムージングを適用
S=spectra(X, sr, t; smoothing=blackmanSmoother)
plot(S[1]; spectraArgs...)
plot(S[2]; spectraArgs...)
plot(S[3]; spectraArgs...)

# S[1]のすべての系列に対して1Hzバンドパス領域でスペクトルをプロット
plot(bands(S[1], 1))

# スレピアンのマルチテーパリングを使用
S=spectra(X, sr, wl; tapering=slepians(sr, wl, 1.))
plot(S[1]; spectraArgs...)

# オブジェクト間の平均スペクトルをプロット
plot(mean(s.y for s ∈ S))


```
