```julia
(1)
function meanDirection( 𝐙         :: TFAnalyticSignalVector,
                        frange    :: fInterval,
                        trange    :: tInterval;
                    nonlinear :: Bool       = false,
                    mode      :: Function   = extract,
                    func      :: Function   = identity,
                    w         :: Vector     = [],
                    check     :: Bool       = true)

(2)
function meanDirection( 𝐱      :: Vector{Vector{T}},
                        sr     :: Int,
                        wl     :: Int,
                        frange :: fInterval,
                        trange :: tInterval,
                     bandwidth :: IntOrReal    = 2;
                 nonlinear     :: Bool         = false,
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

この関数は、[`concentration`](@ref) 関数の2つの対応するメソッドと全く同じ構文を使用する2つのメソッドを特徴としています。すべての引数は、そこにおいて正確に同じ意味を持ちます。出力のみが異なります：

オプションのキーワードパラメータ `nonlinear` が false（デフォルト）の場合、[(加重)平均方向](@ref) 測定を推定し、それ以外の場合は[(加重)位相平均方向](@ref) 測定を推定します。

**エイリアス**: mdir

**関連項目**: [`meanAmplitude`](@ref), [`concentration`](@ref), [timefrequencybi.jl](@ref)。

**例**: [`meanAmplitude`](@ref) の例を参照してください。
