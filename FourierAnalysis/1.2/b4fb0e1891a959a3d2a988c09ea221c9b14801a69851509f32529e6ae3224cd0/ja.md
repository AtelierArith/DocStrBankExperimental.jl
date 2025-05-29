```julia
(1)
function meanAmplitude( 𝐀      :: TFAmplitudeVector,
                        frange :: fInterval,
                        trange :: tInterval;
                    mode   :: Function = extract,
                    func   :: Function = identity,
                    w      :: Vector   = [],
                    check  :: Bool     = true)

(2)
function meanAmplitude( 𝐙 :: TFAnalyticSignalVector,
                    < same arguments as method (1) >

(3)
function meanAmplitude( 𝐱      :: Vector{Vector{T}},
                        sr     :: Int,
                        wl     :: Int,
                        frange :: fInterval,
                        trange :: tInterval,
                     bandwidth :: IntOrReal    = 2;
                 mode          :: Function     = extract,
                 func          :: Function     = identity,
                 w             :: Vector       = [],
                 check         :: Bool         = true,
                 filtkind      :: FilterDesign = Butterworth(2),
                 fmin          :: IntOrReal    = bandwidth,
                 fmax          :: IntOrReal    = sr÷2,
                 fsmoothing    :: Smoother     = noSmoother,
                 tsmoothing    :: Smoother     = noSmoother,
                 planner       :: Planner      = getplanner,
                 ⏩           :: Bool         = true) where T<:Real

```

**エイリアス**: mamp

(1)

[TFAmplitudeVector](@ref) オブジェクトを与えられた場合、これらのオブジェクト全体にわたる [(加重) 平均振幅](@ref) 測定値を推定します。`𝐀` 内のすべてのオブジェクトの時間-周波数平面は一致している必要があります。

**引数**:

`frange` と `trange` は、推定が求められる時間-周波数領域を定義します。`frange` は [fInterval](@ref) 型で、フィルタバンクの中心周波数を制限します。`trange` は [tInterval](@ref) 型で、時間サンプルを制限します。全体の時間-周波数平面で推定を得るには、両方の引数にコロン (:) 記号を使用します。

**オプションのキーワード引数**

`mode=extract` が渡された場合（デフォルト）、選択した時間-周波数領域内のすべての点に対して測定が計算されます。`mode=mean` が渡された場合、これらの点の平均（グランドアベレージ）に対して計算されます。[`extract`](@ref) および [`mean`](@ref) 関数は *FourierAnalysis* の [汎用メソッド](@ref) です。

**注意**: `mode=mean` の場合、関数の出力は常に実数ですが、`mode=extract` の場合、出力は実数、実数の行または列ベクトル、または実数の行列になる可能性があります。これは選択した時間-周波数領域の形状によります。

`func` 引数で関数を渡すことで、[独自の時間-周波数測定値を導出することができます](@ref)。

`w` は、各入力オブジェクトに関連付けられた非負の実数の重みのベクトルである可能性があります。デフォルトでは、測定の非加重バージョンが計算されます。

`check` が true（デフォルト）の場合、列記号が渡された場合にチェックします。

  * `frange` 引数として、すべての入力オブジェクトが同じ行数（中心周波数）を持っていること。
  * `trange` 引数として、すべての入力オブジェクトが同じ列数（時間サンプル）を持っていること。

いずれかのチェックが失敗した場合、エラーメッセージを印刷し、`Nothing` を返します。他の範囲チェックは行われません。

(2)

[TFAnalyticSignalVector](@ref) オブジェクトを与えられた場合、`𝐙` 内のすべてのオブジェクトの振幅を計算し、メソッド (1) に従ってこれらのオブジェクト全体にわたる [(加重) 平均振幅](@ref) 測定値を推定します。さらに、このメソッドを使用する場合、`𝐙` 内のすべての [TFAnalyticSignal](@ref) は `linear` でなければならず、`check` が true（デフォルト）の場合、これが満たされないとエラーを印刷し、`Nothing` を返します。メソッド (1) によって行われる `frange` および `trange` のチェックもこのメソッドによって行われます。

(3)

`𝐱` 内のすべてのデータベクトルの振幅を推定し、[`TFamplitude`](@ref) コンストラクタを呼び出してから、メソッド (1) に従って構築された振幅オブジェクト全体にわたる [(加重) 平均振幅](@ref) 測定値を推定します。

`frange`、`trange`、`mode`、`func`、`w` および `check` は、メソッド (1) と同じ意味を持ちます。他の引数は [`TFamplitude`](@ref) コンストラクタに渡され、意味については読者に参照されます。

**参照**: [`concentration`](@ref)、[`meanDirection`](@ref)、[timefrequencybi.jl](@ref)。

**例**:

```julia
using FourierAnalysis

# 100 のデータベクトルを生成
sr, t, bandwidth=128, 512, 2
h=taper(harris4, t)
𝐱=[sinusoidal(2, 10, sr, t, 0).*h.y+randn(t) for i=1:100]

𝐘=TFanalyticsignal(𝐱, sr, t, bandwidth; fmax=32)
𝐀=TFamplitude(𝐘)

# TFAnalyticSignalVector オブジェクトからの TF 領域における平均振幅
MAmp=meanAmplitude(𝐘, (4, 16), :)
heatmap(MAmp; c=:fire) # y 軸ラベルは正しくありません

# TFAmplitudeVector オブジェクトからの TF 領域における平均振幅
MAmp=meanAmplitude(𝐀, (4, 16), :)

# データから直接の TF 領域における平均振幅
MAmp=meanAmplitude(𝐱, sr, t, (4, 16), :, bandwidth)

# 注意: 上記では、解析信号オブジェクトはすべて
# 線形である必要があります。なぜなら、meanAmplitude は振幅から計算され、
# 非線形解析信号の振幅は均一に 1 に等しいからです。

# これらの計算は、TF 領域での平均を取得することで得られます。例えば、
MAmp=meanAmplitude(𝐘, (4, 16), :; mode=mean) # 実数を出力

# また、平滑化された振幅に対しても取得できます。例えば、
MAmp=meanAmplitude(𝐱, sr, t, (4, 16), :;
                   fsmoothing=blackmanSmoother,
                   tsmoothing=blackmanSmoother)
# または、同等に、エイリアス `mamp` を使用して、
MAmp=mamp(smooth(blackmanSmoother, blackmanSmoother, 𝐀), (4, 16), :)

# 他の単変量測定に対しても同様の構文が使用されます。例えば、
# TFAnalyticSignalVector オブジェクトからの TF 領域での集中度の平均
ConM=concentration(𝐘, (4, 16), (128, 384); mode=mean)

# データから直接の TF 領域での集中度（エイリアス `con` を使用）
ConE=con(𝐱, sr, t, (4, 16), (128, 384), bandwidth; mode=extract)
heatmap(Con; c=:fire) # y 軸ラベルは正しくありません

注意: ConM は mean(ConE) と全く同等ではありません！

# データから直接の TF 領域での平均方向
MDir=meanDirection(𝐱, sr, t, (4, 16), :, bandwidth; mode=mean)

# TFAnalyticSignalVector オブジェクトからの TF 領域での平均方向
MDir=meanDirection(𝐘, (4, 16), :)

# 非線形の対応物について:
# データから直接の TF 領域での位相集中度
Con=concentration(𝐱, sr, t, (8, 12), :; nonlinear=true)

# 単一の TF 点での位相集中度
Con=concentration(𝐱, sr, t, 10, 256; nonlinear=true)

# データから直接の TF 領域での位相平均方向
# エイリアス `mdir` を使用
MDir=mdir(𝐱, sr, t, (8, 12), :; mode=mean, nonlinear=true)

# 線形解析信号オブジェクトから非線形測定を計算しようとするとエラーが発生します
# （REPL を参照）、例えば、
Con=con(𝐘, (8, 12), (1, 512); mode=mean, nonlinear=true)

# 解析信号オブジェクトから非線形測定を計算するためには、
# まず非線形解析信号オブジェクトを計算する必要があります：
𝐘=TFanalyticsignal(𝐱, sr, t, bandwidth; fmax=32, nonlinear=true)

# その後、例えば位相集中度を取得できます
Con=con(𝐘, (8, 12), :; mode=mean, nonlinear=true)

# そして位相平均方向
MDir=meanDirection(𝐘, (8, 12), :; nonlinear=true)
```
