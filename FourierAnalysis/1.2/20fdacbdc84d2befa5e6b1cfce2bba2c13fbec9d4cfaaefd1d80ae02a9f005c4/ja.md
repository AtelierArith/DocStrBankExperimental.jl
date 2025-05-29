```julia
(1)
function TFphase(Z :: TFAnalyticSignal;
            func      :: Function = identity,
            unwrapped :: Bool     = false)

(2)
function TFphase(𝐙 :: TFAnalyticSignalVector;
            func      ::Function = identity,
            unwrapped ::Bool     = false)

(3)
function TFphase(x         :: Vector{T},
                 sr        :: Int,
                 wl        :: Int,
                 bandwidth :: IntOrReal = 2;
           unwrapped  :: Bool         = false,
           func       :: Function     = identity,
           filtkind   :: FilterDesign = Butterworth(2),
           fmin       :: IntOrReal    = bandwidth,
           fmax       :: IntOrReal    = sr÷2,
           nonlinear  :: Bool         = false,
           fsmoothing :: Smoother     = noSmoother,
           tsmoothing :: Smoother     = noSmoother,
           planner    :: Planner      = getplanner,
           ⏩        :: Bool         = true) where T<:Real

(4)
function TFphase(𝐱 :: Vector{Vector{T}},
                < same arguments as method (3) >
```

(1)

[TFPhase](@ref) オブジェクトを構築し、[TFAnalyticSignal](@ref) オブジェクト `Z` の位相を計算します。デフォルトでは、位相は $[−π, π]$ で表されます。

オプションのキーワード引数 `unwrapped` が true の場合（デフォルトは false）、位相はアンラップされ、すなわち、これは $[0, 2π]$ で表されるときに時間次元に沿った位相の累積和を保持します。

オプションのキーワード引数 `func` は、出力のデータ行列に要素ごとに適用される関数です。デフォルトでは、`identity`（何もしない）関数が適用されます。`unwrapped` が true の場合、関数はアンラップされた位相に適用されます。

(2)

[TFAnalyticSignalVector](@ref) オブジェクトから [TFPhaseVector](@ref) オブジェクトを構築し、`𝐙` 内のすべての [TFAnalyticSignal](@ref) オブジェクトに対してメソッド (1) を実行します。

(3)

[`TFanalyticsignal`](@ref) を呼び出して、実信号ベクトル `x` の時間周波数解析信号を取得し、`x` の時間周波数位相（引数）を保持する [TFPhase](@ref) オブジェクトを構築します。

すべての引数は、解析信号の推定を調整するために使用されますが、`unwrapped`、`func`、`fsmoothing` および `fsmoothing` は除きます。

`unwrapped` はメソッド (1) および (2) と同じ意味を持ちます。

`func` は位相データ行列出力に適用されるオプションの関数です。`unwrapped` が true の場合、アンラップされた位相に適用されます。

時間周波数領域で解析信号を推定するために、この関数は [`TFanalyticsignal`](@ref) コンストラクタ（そこにあるメソッド (1)）を呼び出し、`fsmoothing` および `tsmoothing` 引数は両方とも `noSmoother` に設定されます。`fsmoothing` および `fsmoothing` は、`unwrapped` が true の場合に位相を平滑化するために使用されます。

代わりに平滑化された解析信号の位相推定を取得するには、[`TFanalyticsignal`](@ref) コンストラクタに [Smoother](@ref) を渡して [TFAnalyticSignal](@ref) オブジェクトを作成し、その後メソッド (1) を使用して位相を取得します。

他のすべての引数の意味については、関数 [`TFanalyticsignal`](@ref) に渡される引数について、そこにあるドキュメントを参照してください。

(4)

実信号ベクトルのベクトル `𝐱` から [TFPhaseVector](@ref) オブジェクトを構築し、それらすべてに対してメソッド (3) を実行します。信号のベクトルに対して時間周波数解析信号を推定するために、[`TFanalyticsignal`](@ref) のメソッド (2) が呼び出されます。

**参照**: [`TFanalyticsignal`](@ref)、[TFPhase](@ref)。

**関連**: [`phase`](@ref)、[`unwrapPhase`](@ref)、[`polar`](@ref)。

**例**: [`TFanalyticsignal`](@ref) の例を参照してください。
