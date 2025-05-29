```julia
(5)
function coherence(𝐙₁     :: TFAnalyticSignalVector,
                   𝐙₂     :: TFAnalyticSignalVector,
                   frange :: fInterval,
                   trange :: tInterval;
              nonlinear :: Bool     = false,
              allkinds  :: Bool     = false,
              mode      :: Function = extract,
              func      :: Function = identity,
              w         :: Vector   = [],
              check     :: Bool     = true)

(6)
function coherence(𝐱₁        :: Vector{Vector{T}},
                   𝐱₂        :: Vector{Vector{T}},
                   sr        :: Int,
                   wl        :: Int,
                   frange    :: fInterval,
                   trange    :: tInterval,
                   bandwidth :: IntOrReal = 2;
              nonlinear  :: Bool         = false,
              allkinds   :: Bool         = false,
              mode       :: Function     = extract,
              func       :: Function     = identity,
              w          :: Vector       = [],
              filtkind   :: FilterDesign = Butterworth(2),
              fmin       :: IntOrReal    = bandwidth,
              fmax       :: IntOrReal    = sr÷2,
              fsmoothing :: Smoother     = noSmoother,
              tsmoothing :: Smoother     = noSmoother,
              planner    :: Planner      = getplanner,
              ⏩        :: Bool         = true) where T<:Real

```

**エイリアス**: coh

オプションのキーワードパラメータ `nonlinear` が false（デフォルト）の場合、線形 [(加重) コヒーレンス](@ref) 測定を推定します。それ以外の場合は、[(加重) 位相集中](@ref) 測定を推定します。

オプションのキーワード引数 `allkinds` が true の場合、すべての5種類の [コヒーレンス](@ref) が返されます。この場合、出力は `Coherence` 行列の5タプルで、順番は次の通りです：

  * *全体* コヒーレンス、
  * *実* コヒーレンス、
  * *瞬時* コヒーレンス、
  * *虚* コヒーレンス、
  * *遅延* コヒーレンス。

`allkinds` が false（デフォルト）の場合、*全体*（古典的）コヒーレンスのみが単一の `Coherence` 行列として返されます。

(5) 望ましい測定は、`𝐙` 内の [TFAnalyticSignal](@ref) オブジェクトを平均化することで得られます。このメソッドは事前に計算された解析信号オブジェクトを使用するため、それらの `.nonlinear` フィールドは、この関数に渡された `nonlinear` 引数と一致する必要があります。

`frange`、`trange`、`w`、`mode` および `func` は [`meanAmplitude`](@ref) 関数と同じ意味を持ちますが、2つの可能な `mode` 関数、すなわち [`extract`](@ref) と [`mean`](@ref) は、この関数では複素数に対して操作します。

[`meanAmplitude`](@ref) 関数で実行されるチェックは、ここでも実行されます。さらに、`check` が true の場合、次のことも確認します：

  * `nonlinear` が true の場合、`𝐙` 内のすべてのオブジェクトが非線形であること；
  * `nonlinear` が false の場合、`𝐙` 内のすべてのオブジェクトが線形であること。

いずれかのチェックが失敗した場合、エラーメッセージを表示し、`Nothing` を返します。

(6) `𝐱` 内のすべてのデータベクトルの解析信号を推定し、[`TFanalyticsignal`](@ref) コンストラクタを呼び出してから、メソッド (5) を使用して望ましい測定を得ます。

`frange`、`trange`、`mode`、`func`、`w` および `check` は [`meanAmplitude`](@ref) 関数と同じ意味を持ちます。他の引数は [`TFanalyticsignal`](@ref) コンストラクタに渡され、これらの動作を理解するために読者は参照されるべきです。

**関連情報**: [`meanAmplitude`](@ref)、[`meanDirection`](@ref)、[timefrequencybi.jl](@ref)。

**例**: [`comodulation`](@ref) 関数の例を参照してください。
