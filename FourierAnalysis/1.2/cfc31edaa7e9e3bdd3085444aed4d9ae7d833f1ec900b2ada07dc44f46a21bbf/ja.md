```julia
(1)
function TFanalyticsignal(x         :: Vector{T},
                          sr        :: Int,
                          wl        :: Int          = 0,
                          bandwidth :: IntOrReal    = 2;
                      fmin          :: IntOrReal    = bandwidth,
                      fmax          :: IntOrReal    = sr÷2,
                      filtkind      :: FilterDesign = Butterworth(2),
                      nonlinear     :: Bool         = false,
                      fsmoothing    :: Smoother     = noSmoother,
                      tsmoothing    :: Smoother     = noSmoother,
                      planner       :: Planner      = getplanner,
                      ⏩           :: Bool         = true) where T<:Real

(2)
function TFanalyticsignal(𝐱         :: Vector{Vector{T}},
                      <same arguments as method (1)>

```

(1)

サンプリングレート `sr` が与えられたとき、単変量データ `x` から [TFAnalyticSignal](@ref) オブジェクトを構築します。つまり、実ベクトル `x` の時間周波数表現です。

次の三つの操作を行う三つの関数を連続して呼び出します：

i. データをバンクのパスバンドフィルタを通過させ、関数 [`filterbank`](@ref) を呼び出します。

ii. 関数 [`analyticsignal`](@ref) を呼び出して解析信号を計算します（そこにあるメソッド (1)）。

iii. 要求された場合、関数 [`smooth`](@ref) を呼び出して時間および/または周波数次元に沿って解析信号を平滑化します。

これらの関数に渡される引数は次の通りです：

| filterbank  | analyticsignal |    smooth    |
|:-----------:|:--------------:|:------------:|
|     `x`     |      `wl`      | `fsmoothing` |
|    `sr`     |  `nonlinear`   | `tsmoothing` |
| `bandwidth` |   `planner`    |              |
| `filtkind`  |      `⏩`       |              |
|   `fmin`    |                |              |
|   `fmax`    |                |              |
|     `⏩`     |                |              |

各関数のドキュメントを参照して、各引数の意味を学んでください。

デフォルトでは、`wl` 引数は `length(x)` に設定されています。

`⏩` が true の場合（デフォルト）、フィルタリングと解析信号の計算は、バンドパス領域を通じてマルチスレッドで行われます。これは、領域の数が Julia に指示されたスレッドの数の少なくとも二倍である限りです。詳細は [Threads](@ref) を参照してください。

(2)

サンプリングレート `sr` が与えられたとき、単変量データのベクトル `𝐱` から [TFAnalyticSignalVector](@ref) オブジェクトを構築します。つまり、`𝐱` のベクトルの時間周波数表現からです。

このメソッドは、次の例外を除いてメソッド (1) と同様に動作します：

デフォルトでは、`wl` 引数は `𝐱` の各ベクトルに対して `length(x)` に設定されています。別の値が与えられた場合、それはすべてのベクトルに使用されます。

`⏩` が true の場合（デフォルト）、メソッドは `𝐱` のベクトル間でマルチスレッドモードで実行されます。これは、ベクトルの数が Julia に指示されたスレッドの数の少なくとも二倍である限りです。そうでない場合、このメソッドはメソッド (1) のように各解析信号推定をマルチスレッドモードで実行しようとします。詳細は [Threads](@ref) を参照してください。

`Planner` が明示的に引数として渡されない場合、FFTW プランは一度計算され、すべての解析信号推定に適用されます。

**参照**: [`filterbank`](@ref), [`analyticsignal`](@ref), [`smooth`](@ref)。

**例**:

```julia
using Plots, FourierAnalysis

# データを生成
sr, t, bandwidth=128, 512, 2
h=taper(harris4, t)
x1=sinusoidal(10, 8, sr, t, 0)
x2=sinusoidal(10, 19, sr, t, 0)
x=Vector((x1+x2).*h.y+randn(t))
y1=sinusoidal(10, 6, sr, t, 0)
y2=sinusoidal(10, 16, sr, t, 0)
y=Vector((y1+y2).*h.y+randn(t))
plot([x, y])

# x のための TFAnalyticSignal オブジェクト (メソッド (1))
Y = TFanalyticsignal(x, sr, sr*4; fmax=32)

# x と y のための TFAnalyticSignal オブジェクトのベクトル (メソッド (2))
𝒀 = TFanalyticsignal([x, y], sr, sr*4; fmax=32)

# （コメントを短縮するために: TF=時間周波数、AS=解析信号）

# 最初のオブジェクトの TF 領域 (8:12Hz およびサンプル 1:128) における平均 AS
m=mean(𝒀[1], (8, 12), (1, 128)) # 複素数を出力

# 最初のオブジェクトの TF 領域 (8:12Hz およびサンプル 1:128) における AS を抽出
E=extract(𝒀[1], (8, 12), (1, 128)) # 複素行列を出力

# 二つのオブジェクトの TF 領域 (8:12Hz およびサンプル 1:128) における平均 AS
𝐦=mean(𝒀, (8, 12), (1, 128)) # 複素数のベクトルを出力
# 𝒀 の二つのオブジェクトの均一性を確認せずに同じ計算を行う（速い）
𝐦=mean(𝒀, (8, 12), (1, 128); check=false)

# 二つのオブジェクトの TF 領域 (8:12Hz およびサンプル 1:128) における AS を抽出
𝐄=extract(𝒀, (8, 12), (8, 12)) # 複素行列のベクトルを出力

# x の AS の実部をプロット（単位 recipes.jl を参照）

# プロットのための最初の有用な属性を集める
using Plots.Measures
tfArgs=(right_margin = 2mm,
        top_margin = 2mm,
        xtickfont = font(10, "Times"),
        ytickfont = font(10, "Times"))

heatmap(tfAxes(Y)..., real(Y.y);
        c=:fire, tfArgs...)

# ...虚部
heatmap(tfAxes(Y)..., imag(Y.y);
        c=:bluesreds, tfArgs...)

# ...振幅
heatmap(tfAxes(Y)..., amplitude(Y.y);
        c=:amp, tfArgs...)

# ...周波数と時間で平滑化された AS の振幅
heatmap(tfAxes(Y)..., amplitude(smooth(hannSmoother, hannSmoother, Y).y);
        c=:fire, tfArgs...)

# ...位相
heatmap(tfAxes(Y)..., phase(Y.y);
        c=:bluesreds, tfArgs...)

# AS から TFAmplitude オブジェクトを生成
A=TFamplitude(Y)
# そしてプロットする（異なる色で）
heatmap(tfAxes(A)..., A.y;
        c=:fire, tfArgs...)

# TFPhase オブジェクトを生成
ϴ=TFphase(Y)
# そしてプロットする（カスタムカラーで）
heatmap(tfAxes(ϴ)..., ϴ.y;
        c=:fire, tfArgs...)

# [0, 2π] の位相を計算してプロット
heatmap(tfAxes(Y)..., TFphase(Y; func=x->x+π).y;
        c=:amp, tfArgs...)

# アンラップされた位相を計算してプロット
heatmap(tfAxes(Y)..., TFphase(Y; unwrapped=true).y;
        c=:amp, tfArgs...)

# 時間周波数 AS を平滑化: 周波数を平滑化
Z=smooth(blackmanSmoother, noSmoother, Y)

# 平滑化された解析信号の振幅をプロット
heatmap(tfAxes(Z)..., amplitude(Z.y);
        c=:amp, tfArgs...)

# 同等ではない (!)、振幅オブジェクトを作成してそれを平滑化する：
# この場合、振幅が平滑化され、AS ではない
A=smooth(blackmanSmoother, noSmoother, TFamplitude(Y))
heatmap(tfAxes(A)..., A.y;
        c=:fire, tfArgs...)

# 生の位相推定を平滑化することは不適切です
# 位相は不連続関数であるため、しかし位相がアンラップされている場合は
# 位相を平滑化することは意味があります。
heatmap(tfAxes(Y)...,
        smooth(blackmanSmoother, noSmoother, TFphase(Y; unwrapped=true)).y;
        c=:amp, tfArgs...)

# AS を平滑化: 周波数と時間の両方を平滑化
E=smooth(blackmanSmoother, blackmanSmoother, Y)

# 平滑化された解析信号の振幅をプロット
heatmap(tfAxes(E)..., amplitude(E.y);
        c=:fire, tfArgs...)

# 平滑化された解析信号の位相をプロット
heatmap(tfAxes(E)..., phase(E.y);
        c=:bluesreds, tfArgs...)

# 同等ではない (!)、振幅と位相オブジェクトを作成してそれらを平滑化する
A=smooth(blackmanSmoother, blackmanSmoother, TFamplitude(Y))
heatmap(tfAxes(A)..., A.y;
        c=:fire, tfArgs...)

ϴ=smooth(blackmanSmoother, blackmanSmoother, TFphase(Y, unwrapped=true))
heatmap(tfAxes(ϴ)..., ϴ.y;
        c=:fire, tfArgs...)

# 再度平滑化
ϴ=smooth(blackmanSmoother, blackmanSmoother, ϴ)
heatmap(tfAxes(ϴ)..., ϴ.y;
        c=:fire, tfArgs...)
# そして再度 ...

# 直接平滑化された AS を作成
Y=TFanalyticsignal(x, sr, t, bandwidth;
                   fmax=32,
                   fsmoothing=hannSmoother,
                   tsmoothing=hannSmoother)

# 平滑化された解析信号の振幅をプロット
heatmap(tfAxes(Y)..., amplitude(Y.y);
        c=:amp, tfArgs...)

# 直接平滑化された振幅を作成
A=TFamplitude(x, sr, t, bandwidth;
              fmax=32,
              fsmoothing=hannSmoother,
              tsmoothing=hannSmoother)

# 平滑化された振幅をプロット
heatmap(tfAxes(A)..., A.y;
        c=:amp, tfArgs...)

# 非線形 AS を持つ TFAnalyticSignal オブジェクトを計算
Y=TFanalyticsignal(x, sr, t, bandwidth; fmax=32, nonlinear=true)

# 非線形であることを確認
Y.nonlinear

# 振幅が今やどこでも 1.0 であることを確認
norm(amplitude(Y.y)-ones(eltype(Y.y), size(Y.y))) # ゼロでなければならない

# 非線形位相をプロット
heatmap(tfAxes(Y)..., phase(Y.y);
        c=:bkr, tfArgs...)

# TFAmplitude オブジェクト A の中心周波数を取得
A.flabels

# 時間周波数領域で振幅を抽出
extract(A, (2, 10), (1, 256)) # 実行列を出力

# 一つの周波数での時間周波数領域で振幅を抽出
extract(A, 10, (1, 256)) # 行ベクトルを出力

# 一つの周波数での一つの時間サンプルで振幅を抽出
extract(A, 10, 12) # または extract(A, 10.0, 12)

# 周波数領域での一つの時間サンプルで振幅を抽出
extract(A, (10, 12), 12) # または extract(A, (10.0, 12.0), 12)

# 一つの時間サンプルとすべての周波数で振幅を抽出
extract(A, :, 12) # （列）ベクトルを出力

# 時間周波数領域での平均を計算：
mean(A, (2, 10), (1, 256)) # 実数を出力
# は次のように等価ですが（ただし効率が悪い場合があります）
mean(extract(A, (2, 10), (1, 256)))

# すべての時間サンプルを抽出するための列記号を使用
extract(A, (2, 10), :)

# これ：
extract(A, :, :)
# はこれと等価です：
A.y
# しかし、すべての周波数を抽出する必要がない場合は、
# 抽出関数を使用して抽出する周波数を制御してください：
# これ
extract(A, (4, 5), 10)
# はこれと等価ではありません
A.y[4:5, 10]
# なぜなら `extract` 関数は求められた周波数（Hz）に対応する正しい行を見つけるからです。
# 一方、A.y[4:5, 10] は TF 振幅オブジェクトの要素 [4:5, 10] を返すだけです。

# A の最初の中心周波数が 2Hz であるにもかかわらず、
# そのバンドパス領域は 1-3Hz であるため、周波数範囲 1:10 は受け入れられます。
mean(A, (1, 10), (1, 256))
# しかし、これはエラーを引き起こします（REPL を参照）なぜなら 0.5 は範囲外だからです：
mean(A, (0.5, 10), (1, 256))

# 時間範囲のためのコロン記号を使用
a=mean(A, (1, 10), :)
# 時間範囲のための整数を使用（特定のサンプルを示す）
a=mean(A, (1, 10), 16)

# 周波数範囲のためのコロン記号を使用
a=mean(A, :, (1, 16))
# 周波数範囲のための実数を使用
a=mean(A, 8.5, (1, 16))

# NB: `extract` と `mean` 関数は同じ構文で動作します
#     TFAnalyticSignal、TFAmplitude、TFPhase オブジェクトに対して。
```
