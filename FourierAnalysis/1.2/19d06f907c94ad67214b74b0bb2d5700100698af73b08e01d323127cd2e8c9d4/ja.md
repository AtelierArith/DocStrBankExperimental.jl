```julia
(1)
function comodulation( 𝐡₁     :: TFAmplitudeVector,
                       𝐡₂     :: TFAmplitudeVector,
                       frange :: fInterval,
                       trange :: tInterval;
                  mode  :: Function = extract,
                  func  :: Function = identity,
                  w     :: Vector = [],
                  check :: Bool   = true) =

(2)
function comodulation( 𝐳₁     :: TFAnalyticSignalVector,
                       𝐳₂     :: TFAnalyticSignalVector,
    < arguments frange, trange, mode, func, w and check as in method (1) >

(3)
function comodulation(𝐱₁        :: Vector{Vector{T}},
                      𝐱₂        :: Vector{Vector{T}},
                      sr        :: Int,
                      wl        :: Int,
                      frange    :: fInterval,
                      trange    :: tInterval,
                      bandwidth :: IntOrReal    = 2;
                mode            :: Function     = extract,
                func            :: Function     = identity,
                w               :: Vector       = [],
                filtkind        :: FilterDesign = Butterworth(2),
                fmin            :: IntOrReal    = bandwidth,
                fmax            :: IntOrReal    = sr÷2,
                fsmoothing      :: Smoother     = noSmoother,
                tsmoothing      :: Smoother     = noSmoother,
                planner         :: Planner      = getplanner,
                ⏩             :: Bool         = true) where T<:Real

```

**エイリアス**: com

(1)

[TFAmplitudeVector](@ref) オブジェクトのペアを与えられた場合、[(加重)コモジュレーション](@ref) 測定値を推定します。`𝐀₁` と `𝐀₂` は同じ数のオブジェクトを保持し、すべてのオブジェクトの時間周波数平面は合同である必要があります。

**引数**:

`frange` と `trange` は [`meanAmplitude`](@ref) メソッドと同じ意味を持ちます。

**オプションのキーワード引数**

`mode`、`func`、および `check` は [`meanAmplitude`](@ref) メソッドと同じ意味を持ちます。

`w` は、各入力オブジェクトのペアに関連付けられた非負の実数の重みのベクトルである可能性があります。デフォルトでは、測定値の重みなしバージョンが計算されます。

(2)

[TFAnalyticSignalVector](@ref) オブジェクトのペアを与えられた場合、すべてのオブジェクトの振幅を計算し、メソッド (1) に従って [(加重)コモジュレーション](@ref) を推定します。メソッド (1) と同様に、`𝐙₁` と `𝐙₂` は同じ数のオブジェクトを保持し、すべてのオブジェクトの時間周波数平面は合同である必要があります。さらに、このメソッドを使用する場合、`𝐙₁` と `𝐙₂` のすべての [TFAnalyticSignal](@ref) オブジェクトは `linear` でなければならず、`check` が true (デフォルト) の場合、そうでないとエラーを印刷し、`Nothing` を返します。メソッド (1) によって実行される `frange` と `trange` のチェックもこのメソッドによって実行されます。

(3)

`𝐱₁` と `𝐱₂` のすべてのデータベクトルの振幅を推定し、[`TFamplitude`](@ref) コンストラクタを呼び出してから、メソッド (1) に従って構築された振幅オブジェクト間で [(加重)コモジュレーション](@ref) 測定値を推定します。

`frange`、`trange`、`mode`、`func`、`w`、および `check` はメソッド (1) と同じ意味を持ちます。他の引数は [`TFamplitude`](@ref) コンストラクタに渡され、その意味については読者に参照されます。

FFT計算のための `planner` が提供されていない場合、1回計算され、すべての振幅推定に適用されます。

**参照**: [`coherence`](@ref)、[timefrequencybi.jl](@ref)。

**例**:

```julia
using FourierAnalysis

# データベクトルの100ペアを生成
sr, t, bandwidth=128, 512, 2
h=taper(harris4, t)
𝐱₁=[sinusoidal(2, 10, sr, t, 0).*h.y+randn(t) for i=1:100]
𝐱₂=[sinusoidal(2, 10, sr, t, 0).*h.y+randn(t) for i=1:100]

# それらの（線形）解析信号を計算
𝐘₁=TFanalyticsignal(𝐱₁, sr, wl, bandwidth; fmax=32, nonlinear=false)
𝐘₂=TFanalyticsignal(𝐱₂, sr, wl, bandwidth; fmax=32, nonlinear=false)

# それらの振幅を計算
𝐀₁=TFamplitude(𝐘₁)
𝐀₂=TFamplitude(𝐘₂)

# TFAnalyticSignal オブジェクトから TF 領域での Com 平均を計算
# 𝐘₁ と 𝐘₂ は線形でなければならない
Com=comodulation(𝐘₁, 𝐘₂, (8, 12), :; mode=mean)

# TFAmplitudeVector オブジェクトから TF 領域での Com 平均を計算
# 𝐀₁ と 𝐀₂ は線形でなければならない
Com=comodulation(𝐀₁, 𝐀₂, (8, 12), :; mode=mean)

# データから直接 TF 領域での Com 平均を計算
# この場合、線形性について心配する必要はありません
Com=comodulation(𝐱₁, 𝐱₂, sr, wl, (8, 12), :, bandwidth; mode=mean)

# スムーズな振幅からコモジュレーションを計算:
Com=comodulation(𝐱₁, 𝐱₂, sr, wl, (8, 12), :, bandwidth;
                 mode=mean,
                 fsmoothing=blackmanSmoother,
                 tsmoothing=blackmanSmoother)

# FFTW プランを事前に計算することで、より速くすることができます。
# これは、コモジュレーション関数を何度も呼び出す必要がある場合に便利です
plan=Planner(plan_patient, 5, wl, Float64, true)
Com=comodulation(𝐱₁, 𝐱₂, sr, wl, (8, 12), :, bandwidth; mode=mean, planner=plan)

# TFAnalyticSignalVector オブジェクトから TF 領域での Com を計算
Com=comodulation(𝐘₁, 𝐘₂, (8, 12), :; mode=extract)

# TFAmplitudeVector オブジェクトから TF 領域での Com を計算
Com=comodulation(𝐀₁, 𝐀₂, (8, 12), :; mode=extract)

# データから直接 TF 領域での Com を計算
Com=comodulation(𝐱₁, 𝐱₂, sr, wl, (8, 12), :, bandwidth; mode=extract)

# これらのすべての操作は、コヒーレンス測定にも行うことができます。たとえば
Coh=coherence(𝐘₁, 𝐘₂, (8, 12), :; mode=mean)

Coh=coherence(𝐘₁, 𝐘₂, (8, 12), :; mode=extract)

# すべての5つのコヒーレンスタイプを計算
Coh=coherence(𝐘₁, 𝐘₂, (8, 12), :; mode=extract, allkinds=true)

# 位相コヒーレンス（位相ロッキング値）
# この測定値は非線形 TFAnalyticSignalVector オブジェクトから得られます
𝐘₁=TFanalyticsignal(𝐱₁, sr, wl, bandwidth; fmax=32, nonlinear=true)
𝐘₂=TFanalyticsignal(𝐱₂, sr, wl, bandwidth; fmax=32, nonlinear=true)

Coh=coherence(𝐘₁, 𝐘₂, (8, 12), :; mode=mean, nonlinear=true)

# またはデータから直接（この場合、非線形性について心配する必要はありません）
Coh=coherence(𝐱₁, 𝐱₂, sr, wl, (8, 12), :, bandwidth; mode=mean, nonlinear=true)

```
