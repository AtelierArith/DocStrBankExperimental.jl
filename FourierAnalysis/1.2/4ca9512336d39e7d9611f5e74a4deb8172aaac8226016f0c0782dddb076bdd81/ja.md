```julia
(1)
function TFamplitude(Z::TFAnalyticSignal;
                func::Function=identity)

(2)
function TFamplitude(𝐙::TFAnalyticSignalVector;
                func::Function=identity)

(3)
function TFamplitude(x         :: Vector{T},
                     sr        :: Int,
                     wl        :: Int,
                     bandwidth :: IntOrReal = 2;
                func       :: Function     = identity,
                filtkind   :: FilterDesign = Butterworth(2),
                fmin       :: IntOrReal    = bandwidth,
                fmax       :: IntOrReal    = sr÷2,
                fsmoothing :: Smoother     = noSmoother,
                tsmoothing :: Smoother     = noSmoother,
                planner    :: Planner      = getplanner,
                ⏩        :: Bool         = true) where T<:Real =

(4)
function TFamplitude(𝐱 :: Vector{Vector{T}},
                < same arguments as method (3) >
```

(1)

[TFAmplitude](@ref)オブジェクトを構築し、[TFAnalyticSignal](@ref)オブジェクト`Z`の振幅を計算します。オプションのキーワード引数`func`は、出力のデータ行列に要素ごとに適用される関数です。デフォルトでは、`identity`（何もしない）関数が適用されます。

(2)

[TFAnalyticSignalVector](@ref)オブジェクトから[TFAmplitudeVector](@ref)オブジェクトを構築し、`𝐙`内のすべての[TFAnalyticSignal](@ref)オブジェクトに対してメソッド(1)を実行します。

(3)

[`TFanalyticsignal`](@ref)を呼び出して、実信号ベクトル`x`の時間-周波数解析信号を取得し、`x`の時間-周波数振幅（モジュラス、しばしば*エンベロープ*と呼ばれる）を保持する[TFAmplitude](@ref)オブジェクトを構築します。

すべての引数は解析信号の推定を調整するために使用されますが、`func`、`fsmoothing`、および`fsmoothing`を除きます：

`func`は、振幅データ行列出力に適用されるオプションの関数です。

時間-周波数領域で解析信号を推定するために、この関数は[`TFanalyticsignal`](@ref)コンストラクタ（そこにあるメソッド(1)）を呼び出し、`fsmoothing`および`tsmoothing`引数を`noSmoother`に設定します。引数`fsmoothing`および`fsmoothing`は、その後、振幅を平滑化するために使用されます。

代わりに平滑化された解析信号の振幅推定を取得するには、[Smoother](@ref)を[`TFanalyticsignal`](@ref)コンストラクタに渡して[TFAmplitude](@ref)オブジェクトを作成し、その後メソッド(1)を使用して振幅を取得します。そのような振幅推定は、例に示すように[`smooth`](@ref)関数を使用してさらに平滑化できます。

他のすべての引数の意味については、関数[`TFanalyticsignal`](@ref)に渡される引数について、そこにあるドキュメントを参照してください。

(4)

実信号ベクトルのベクトル`𝐱`から[TFAmplitudeVector](@ref)オブジェクトを構築し、それらすべてに対してメソッド(3)を実行します。信号のベクトルに対して時間-周波数解析信号を推定するために、[`TFanalyticsignal`](@ref)のメソッド(2)が呼び出されます。

**参照**: [`TFanalyticsignal`](@ref)、[TFAmplitude](@ref)。

**関連**: [`amplitude`](@ref)。

**例**: [`TFanalyticsignal`](@ref)の例を参照してください。
