```julia
(1)
function concentration( 𝐙       :: TFAnalyticSignalVector,
                        frange  :: fInterval,
                        trange  :: tInterval;
                    nonlinear :: Bool     = false,
                    mode      :: Function = extract,
                    func      :: Function = identity,
                    w         :: Vector   = [],
                    check     :: Bool     = true)

(2)
function concentration( 𝐱      :: Vector{Vector{T}},
                        sr     :: Int,
                        wl     :: Int,
                        frange :: fInterval,
                        trange :: tInterval,
                     bandwidth :: IntOrReal    = 2;
                 nonlinear  :: Bool         = false,
                 mode       :: Function     = extract,
                 func       :: Function     = identity,
                 w          :: Vector       = [],
                 check         :: Bool      = true,
                 filtkind   :: FilterDesign = Butterworth(2),
                 fmin       :: IntOrReal    = bandwidth,
                 fmax       :: IntOrReal    = sr÷2,
                 fsmoothing :: Smoother     = noSmoother,
                 tsmoothing :: Smoother     = noSmoother,
                 planner    :: Planner      = getplanner,
                 ⏩        :: Bool         = true) where T<:Real

```

**エイリアス**: con

オプションのキーワード引数 `nonlinear` が false（デフォルト）の場合、[(加重)濃度](@ref)測定を推定し、そうでない場合は[(加重)位相濃度](@ref)測定を推定します。

(1) 目的の測定は、`𝐙`内の[TFAnalyticSignal](@ref)オブジェクトを平均化することで得られます。このメソッドは事前に計算された解析信号オブジェクトを使用するため、それらの `.nonlinear` フィールドはこの関数に渡される `nonlinear` 引数と一致している必要があります。

`frange`、`trange`、`w`、`mode`、および `func` は [`meanAmplitude`](@ref) 関数と同じ意味を持ちますが、注意すべきは、この関数内の2つの可能な `mode` 関数、すなわち [`extract`](@ref) と [`mean`](@ref) が複素数に対して動作することです。

[`meanAmplitude`](@ref) 関数で実行されるチェックはここでも実行されます。さらに、`check` が true の場合、次のことも確認します。

  * `nonlinear` が true の場合、`𝐙`内のすべてのオブジェクトが非線形であること。
  * `nonlinear` が false の場合、`𝐙`内のすべてのオブジェクトが線形であること。

いずれかのチェックが失敗した場合、エラーメッセージを表示し、`Nothing` を返します。

(2) `𝐱`内のすべてのデータベクトルの解析信号を推定し、[`TFanalyticsignal`](@ref) コンストラクタを呼び出してから、メソッド (1) を使用して目的の測定を取得します。

`frange`、`trange`、`mode`、`func`、`w`、および `check` は [`meanAmplitude`](@ref) 関数と同じ意味を持ちます。他の引数は [`TFanalyticsignal`](@ref) コンストラクタに渡され、これらの動作を理解するために読者は参照されるべきです。

**関連情報**: [`meanAmplitude`](@ref)、[`meanDirection`](@ref)、[timefrequencybi.jl](@ref)。

**例**: [`meanAmplitude`](@ref) 関数の例を参照してください。
