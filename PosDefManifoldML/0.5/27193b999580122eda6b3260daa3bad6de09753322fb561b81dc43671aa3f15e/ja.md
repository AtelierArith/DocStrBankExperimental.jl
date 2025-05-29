```julia
mutable struct ENLR <: ENLRmodel
    metric      :: Metric = Fisher;
    alpha       :: Real = 1.0
    pipeline    :: Pipeline
    normalize	:: Union{Function, Tuple, Nothing}
    intercept   :: Bool
    meanISR     :: Union{Hermitian, Nothing, UniformScaling}
    vecRange    :: UnitRange
    featDim     :: Int
    # GLMNet Models
    path        :: GLMNet.GLMNetPath
    cvλ         :: GLMNet.GLMNetCrossValidation
    best        :: GLMNet.GLMNetPath
end
```

ENLR 機械学習モデルは、この可変構造体にカプセル化されています。フィールド：

`.metric` は [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1) 型で、接線空間投影の基準点として使用される平均を計算するために採用されるメトリックです。デフォルトでは、フィッシャーメトリックが採用されます。利用可能なメトリックについては [mdm.jl](@ref) を参照してください。モデルのトレーニングに使用されるデータが正定値行列でなく、ユークリッド特徴ベクトルである場合、`.metric` フィールドは無用です。メトリックを使用するには、*PosDefManifold* パッケージをインストールする必要があります。

`.alpha` は $[0, 1]$ の範囲のハイパーパラメータで、**エラスティックネットモデル**のトレードオフを行います。*α=0* は純粋な **リッジ** モデルを要求し、*α=1* は純粋な **ラッソ** モデルを要求します。デフォルトでは、*α=1* が指定されています（ラッソモデル）。この引数は通常、[`fit`](@ref) 関数にパラメータとして渡され、そこでもデフォルトで *α=1* になります。以下の例を参照してください。

他のすべてのフィールドは、デフォルトの作成者によってモデルの作成時に渡される引数には対応していません。代わりに、モデルが [`fit`](@ref) 関数によって作成されるときに後で埋められます。

フィールド `pipeline` は [`Pipeline`](@ref) 型で、データに適用されるオプションのデータ前処理器のシーケンスを保持します。パイプラインは ML モデルがフィットされるときに学習され、モデルに保存されます。パイプラインがフィットされると、それは [`predict`](@ref) 関数の各呼び出し時にデータに自動的に適用されます。

フィールド `normalize`、`intercept`、`meanISR`、および `vecRange` の内容については、ENLR モデルの [`fit`](@ref) 関数のドキュメントを参照してください。

モデルのトレーニングに使用されるデータが正定値行列である場合、`.featDim` はベクトル化された接線ベクトルの長さです。これは *n(n+1)÷2*（整数除算）で与えられ、*n* はモデルが接線空間にマッピングされた元の PD 行列の次元です。特徴ベクトルを使用してモデルをトレーニングする場合、`.featDim` はこれらのベクトルの長さです。モデルのフィッティングにオプションのキーワード引数 `vecRange` を提供した場合、`.featDim` はそれに応じて減少します。

`.path` は [GLMNet.jl](https://github.com/JuliaStats/GLMNet.jl) パッケージの次の `GLMNetPath` 構造体のインスタンスです。これは、[`fit`](@ref) 関数がオプションのキーワードパラメータ `fitType` = `:path` または = `:all` で呼び出されたときに作成される正則化パスを保持します。

```julia
struct GLMNetPath{F<:Distribution}
    family::F                        # Binomial()
    a0::Vector{Float64}              # 各解の切片値
    betas::CompressedPredictorMatrix # 各解の係数値
    null_dev::Float64                # モデルの null deviance
    dev_ratio::Vector{Float64}       # 各解の R^2 値
    lambda::Vector{Float64}          # 各解の lambda 値
    npasses::Int                     # すべての lambda 値に対するデータの実際のパス数
end
```

`.cvλ` は [GLMNet.jl](https://github.com/JuliaStats/GLMNet.jl) パッケージの次の `GLMNetCrossValidation` 構造体のインスタンスです。これは、[`fit`](@ref) 関数がオプションのキーワードパラメータ `fitType` = `:best`（デフォルト）または = `:all` で呼び出されたときに、最適な lambda ハイパーパラメータを推定するために使用されるクロスバリデーションに関する情報を保持します。

```julia
struct GLMNetCrossValidation
    path::GLMNetPath            # cv パス
    nfolds::Int                 # cv のフォールド数
    lambda::Vector{Float64}     # 各解の lambda 値
    meanloss::Vector{Float64}   # 各解の平均損失
    stdloss::Vector{Float64}    # 平均損失の標準偏差
end
```

`.best` は上記の `GLMNetPath` 構造体のインスタンスです。これは、[`fit`](@ref) 関数が呼び出されたときにデフォルトで作成される、クロスバリデーションによって見つかった最適な lambda パラメータを持つモデルを保持します。

**例**：

```julia
# 注意: デフォルトの作成者を使用してモデルを作成することは可能ですが、
# 一般的には有用ではありません。

using PosDefManifoldML, PosDefManifold

# 空のラッソモデルを作成
m = ENLR(Fisher)

# フィッシャーメトリックがデフォルトメトリックであるため、
# これは次と同等です
m = ENLR()

# logEuclidean メトリックを使用して空のリッジモデルを作成
m = ENLR(logEuclidean; alpha=0)

# 空のモデルは `fit` 関数の最初の引数として渡すことができ、
# モデルをフィットさせます。たとえば、これは `m` と同じ種類の
# リッジモデルをフィットさせ、フィットしたモデルを `m1` に格納します：
m1 = fit(m, PTr, yTr)

# 一般的に、モデルをフィットさせるためにこの機構は必要ありません。
# なぜなら、モデルをその場で作成することで指定できるからです：
m2 = fit(ENLR(logEuclidean; alpha=0), PTr, yTr)

# これは次と同等です
m2 = fit(ENLR(logEuclidean), PTr, yTr; alpha=0)

# モデル `m` がリッジモデルとして作成されたにもかかわらず、
# あなたは `m` を渡し、`alpha` ハイパーパラメータを上書きしました。
# メトリックは、上書きすることはできません。
```
