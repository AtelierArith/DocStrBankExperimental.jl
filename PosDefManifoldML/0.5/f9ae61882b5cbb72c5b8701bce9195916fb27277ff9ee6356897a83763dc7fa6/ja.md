```julia
function fit(model	:: ENLRmodel,
             𝐏Tr	 :: Union{HermitianVector, Matrix{Float64}},
             yTr	:: IntVector;

    # パイプライン（データ変換）
    pipeline    :: Union{Pipeline, Nothing} = nothing,

    # 接線空間への射影のためのパラメータ
    w           :: Union{Symbol, Tuple, Vector} = Float64[],
    meanISR     :: Union{Hermitian, Nothing, UniformScaling} = nothing,
    meanInit    :: Union{Hermitian, Nothing} = nothing,
    vecRange    :: UnitRange = 𝐏Tr isa ℍVector ? (1:size(𝐏Tr[1], 2)) : (1:size(𝐏Tr, 2)),
    normalize	:: Union{Function, Tuple, Nothing} = normalize!,

    # `GLMNet.glmnet` 関数の引数
    alpha           :: Real = model.alpha,
    weights         :: Vector{Float64} = ones(Float64, length(yTr)),
    intercept       :: Bool = true,
    fitType         :: Symbol = :best,
    penalty_factor  :: Vector{Float64} = ones(Float64, _getDim(𝐏Tr, vecRange)),
    constraints     :: Matrix{Float64} = [x for x in (-Inf, Inf), y in 1:_getDim(𝐏Tr, vecRange)],
    offsets         :: Union{Vector{Float64}, Nothing} = nothing,
    dfmax           :: Int = _getDim(𝐏Tr, vecRange),
    pmax            :: Int = min(dfmax*2+20, _getDim(𝐏Tr, vecRange)),
    nlambda         :: Int = 100,
    lambda_min_ratio:: Real = (length(yTr)*2 < _getDim(𝐏Tr, vecRange) ? 1e-2 : 1e-4),
    lambda          :: Vector{Float64} = Float64[],
    maxit           :: Int = 1000000,
    algorithm       :: Symbol = :newtonraphson,
    checkArgs       :: Bool = true,

    # 選択メソッド
    λSelMeth        :: Symbol = :sd1,

    # `GLMNet.glmnetcv` 関数の引数
    nfolds          :: Int = min(10, div(size(yTr, 1), 3)),
    folds           :: Vector{Int} =
    begin
        n, r = divrem(size(yTr, 1), nfolds)
        shuffle!([repeat(1:nfolds, outer=n); 1:r])
    end,
    parallel        :: Bool=true,

    # 一般的および共通のパラメータ
    tol             :: Real = 1e-5,
    verbose         :: Bool = true,
    ⏩              :: Bool = true,
)
```

**2クラス**の弾性ネットロジスティック回帰（[`ENLR`](@ref)）機械学習モデルを作成し、トレーニングデータ`𝐏Tr`（[ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1)型）と対応するラベル`yTr`（[IntVector](@ref)型）を使用してフィットします。フィットしたモデルは[`ENLR`](@ref)構造のインスタンスとして返されます。

!!! warning "クラスラベル"
    ラベルは自然数を使用して提供する必要があります。*すなわち*、最初のクラスには`1`、2番目のクラスには`2`、などです。


接線空間で動作するすべてのMLモデルと同様に、ENLRモデルのフィッティングには、`𝐏Tr`内のすべての行列の平均（バリセンター）を計算し、すべての行列をアイデンティティ行列で平行輸送した後に接線空間に射影し、[vecP](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.vecP)操作を使用してベクトル化することが含まれます。これが完了すると、ENLRがフィットされます。

平均は、オプションの重み`w`を使用して、`model`の`.metric`フィールドに従って計算されます。`model`の`.metric`フィールドは、内部的に[`tsMap`](@ref)関数に渡されます。デフォルトでは、メトリックはフィッシャーメトリックです。メトリックを変更する方法については、以下の例を参照してください。利用可能なメトリックについては、[mdm.jl](@ref)を参照するか、[PosDefManifold.jl](https://marco-congedo.github.io/PosDefManifold.jl/dev/)のドキュメントを直接確認してください。

**オプションのキーワード引数**

`Pipeline`型の`pipeline`が提供されると、条件付けのシーケンスのすべての必要なパラメータがフィットされ、すべての行列がMLモデルをフィットする前に指定されたパイプラインに従って変換されます。パラメータは出力MLモデルに保存されます。フィットされたパイプラインは、出力MLモデルが引数として渡される`predict`(@ref)関数への後続の呼び出しによって自動的に適用されることに注意してください。

デフォルトでは、接線空間にデータを射影するための平均を計算する際に、すべての観測に均等な重みが与えられます。これは、引数`w=:uniform`（または`w=:u`）を渡すことと同等です。引数として次のものを渡すこともできます：

  * `w=:balanced`（または単に`w=:b`）。2つのクラスが不均衡な場合、重みは各クラスの例の数に反比例する方が良いでしょう。これにより、各クラスが平均の計算に均等に寄与します。これは`w=tsWeights(yTr)`を渡すことと同等です。詳細については、[`tsWeights`](@ref)関数を参照してください。
  * `w=v`、ここで`v`は観測のための非負の重みのユーザー定義ベクトルであり、したがって`v`は`yTr`と同じ数の要素を含む必要があります。例えば、`w=[1.0, 1.0, 2.0, 2.0, ...., 1.0]`
  * `w=t`、ここで`t`は実数の重みの2タプルであり、各クラスの1つの重みです。例えば、`w=(0.5, 1.5)`。これは、`w=tsWeights(yTr; classWeights=collect(0.5, 1.5))`を渡すことと同等です。詳細については、[`tsWeights`](@ref)関数を参照してください。

デフォルトでは、`meanISR=nothing`であり、行列を接線空間に射影するために使用される平均の逆平方根（ISR）が計算されます（[`tsMap`](@ref)を参照）。エルミート行列または`I`（アイデンティティ行列）を引数`meanISR`として渡すこともでき、この場合、この行列が平均のISRとして使用されます。渡されたり計算されたりした場合、それはこの関数によって作成されたモデル構造の`.meanISR`フィールドに書き込まれます。`I`を渡すと、行列は再中心化せずにアイデンティティで接線空間に射影されます。これは、行列が前処理パイプラインによって再中心化されている場合に可能です（[`Pipeline`](@ref)を参照）。

`meanISR`が提供されず、`model`の`.metric`フィールドがフィッシャー、logdet0、またはワッサースタインの場合、平均を計算するために使用される反復アルゴリズムの許容誤差は引数`tol`（デフォルト1e-5）に設定されます。また、この場合、これらの反復アルゴリズムの特定の初期化を引数`meanInit`としてエルミート行列として提供できます。

!!! tip "ユークリッドENLRモデル"
    接線空間で動作するMLモデルは、トレーニングデータ`𝐏Tr`として特徴ベクトルの行列を直接渡すことでモデルをフィットさせることができます。この場合、上記のキーワード引数は使用されません。


**次のオプションのキーワード引数は、接線ベクトルおよび一般的な特徴ベクトルのいずれの入力にも作用します**

`UnitRange`がオプションのキーワード引数`vecRange`と共に渡されると、`𝐏Tr`が`Hermitian`行列のベクトルである場合、接線空間に射影された後のこれらの行列のベクトル化は、指定された範囲で与えられた行（または列）のみを対象とします。そうでない場合、`𝐏Tr`が特徴ベクトルが行に配置された行列である場合、指定された範囲で与えられた`𝐏Tr`の列のみが使用されます。前処理パイプラインが使用され、パイプラインが入力行列の次元を変更する場合、引数`vecRange`は無視されます。この場合、新しい次元を使用してデフォルト値に設定されます。この動作を変更することはできません。

`normalize`を使用すると、接線（または特徴）ベクトルを個別に正規化できます。次の3つの関数を渡すことができます。

  * [`demean!`](@ref) 平均を削除するため、
  * [`normalize!`](@ref) ノルムを固定するため（デフォルト）、
  * [`standardize!`](@ref) 平均をゼロに、標準偏差を1に固定するため。

引数`normalize`として、実数の2タプルを渡すこともできます。この場合、数値はベクトルをこれらの制限内に制約するための下限と上限になります - [`rescale!`](@ref)を参照してください。

!!! tip "再スケーリング"
    再スケーリングを希望する場合は、`(-1, 1)`を使用してください。SPD行列の接線ベクトルは正の要素と負の要素を持つためです。`𝐏Tr`が特徴行列で、特徴が正の値のみである場合は、代わりに`(0, 1)`を使用してください。


`normalize`として`nothing`を引数として渡すと、正規化は行われません。

残りのオプションのキーワード引数は、

  * モデルをフィットするための`GLMNet.glmnet`関数に渡される引数です。これらは常に使用されます。
  * `λSelMeth`引数および最適なラムダハイパーパラメータを交差検証で見つけるために`GLMNet.glmnetcv`関数に渡される引数です。これらは`fitType` = `:path`または`= :all`の場合にのみ使用されます。

**GLMNet.jlを使用してモデルをフィットするためのオプションのキーワード引数**

`alpha`: 弾性ネットモデルのトレードオフのためのハイパーパラメータで、$[0, 1]$の範囲にあります。*α=0*は純粋な*リッジ*モデルを要求し、*α=1*は純粋な*ラッソ*モデルを要求します。デフォルトは1.0で、これはラッソモデルを指定します。ただし、入力[`ENLR`](@ref) `model`の`alpha`フィールドに別の値がある場合は、その値が使用されます。ここで引数`alpha`が渡されると、入力`model`の`alpha`フィールドを上書きします。

`weights`: `yTr`と同じサイズの各行列（または特徴ベクトル）の重みのベクトルです。デフォルトはすべての行列に対して1です。

`intercept`: 切片項をフィットさせるかどうか。切片は常にペナルティなしです。デフォルトはtrueです。

`fitType` = `:best`（デフォルト）の場合、与えられたトレーニングデータに対して最適なラムダハイパーパラメータを見つけるために交差検証手順が実行されます。これにより、[`ENLR`](@ref)構造の`.best`フィールドに書き込まれる単一のモデルが見つかります。

`fitType` = `:path`の場合、与えられたトレーニングデータに対してラムダハイパーパラメータのいくつかの値に対する正則化パスが見つかります。これにより、いくつかのモデルが作成され、これらは作成される[`ENLR`](@ref)構造の`.path`フィールドに書き込まれます。これらのモデルは、与えられたトレーニングデータに対して交差検証の観点から最適ではありません。

`fitType` = `:all`の場合、上記の両方のフィットが実行され、作成される[`ENLR`](@ref)構造のすべてのフィールドが埋められます。

`penalty_factor`: モデルが適用される元のPD行列の次元*n(n+1)/2*の長さのベクトルで、接線ベクトル内の各予測子に対するペナルティです。デフォルトではすべて1で、各予測子に均等に重み付けされます。予測子をペナルティなしに指定するには、対応するエントリをゼロに設定します。

`constraints`: 各予測子に対する下限（最初の列）と上限（2番目の列）を指定する*n(n+1)/2* x *2*行列です。デフォルトでは、各予測子に対して[-Inf Inf]です（接線ベクトルの各要素）。

`offset`: 元のGLMNetパッケージのドキュメントを参照してください[🎓](@ref)。

`dfmax`: 最大モデル内の予測子の最大数です。

`pmax`: 任意のモデル内の予測子の最大数です。

`nlambda`: パスに沿って考慮する*λ*の値の数です。

`lambda_min_ratio`: 最小*λ*値を考慮するためのもので、*λ*の値の比率として、ヌルモデル（*すなわち*、切片のみのモデル）の*λ*の値に対してです。観測数が変数数を超える場合、デフォルトは0.0001で、そうでない場合は0.01です。

`lambda`: フィッティングのために考慮する*λ*の値です。デフォルトでは、これは`nlambda`と`lambda_min_ratio`から決定されます。

`maxit`: サイクリック座標降下アルゴリズムの最大反復回数です。収束が達成されない場合、警告が返されます。

`algorithm`: 正則化パスを見つけるために使用されるアルゴリズムです。可能な値は`:newtonraphson`（デフォルト）と`:modifiednewtonraphson`です。

これらの引数に関する詳細については、GLMNetパッケージのリソースを参照してください[🎓](@ref)。

!!! warning "次元の変更の可能性"
    提供された引数`penalty_factor`、`constraints`、`dfmax`、`pmax`、および`lambda_min_ratio`は、前処理`pipeline`が引数として渡され、パイプラインが入力行列の次元を変更する場合、無視されます。この場合、これらは新しい次元を使用してデフォルト値に設定されます。提供された値を強制的に使用するには、`checkArgs`をfalseに設定します（デフォルトはtrueです）。ただし、この場合、上記のすべての引数に対して適切な値を提供する必要があります。


**交差検証によって最適なモデルを見つけるためのオプションのキーワード引数**

`λSelMeth` = `:sd1`（デフォルト）、最適なモデルは、最小値の1標準偏差内で最も高い`cvλ.meanloss`を許可するモデルとして定義されます。そうでない場合は、最小の`cvλ.meanloss`を許可するモデルとして定義されます。モデルを選択する際には、存在する場合、切片項のみのモデルは無視されます。モデル構造の`.cvλ`フィールドの説明については、[`ENLRmodel`](@ref)を参照してください。

引数`nfolds`、`folds`、および`parallel`は、`GLMNet.glmnetcv`関数に`⏩`引数と共に渡されます。詳細については、GLMNetのリソースを参照してください[🎓](@ref)。

`tol`: 接線空間に射影するための平均を計算するための収束基準（メトリックが反復アルゴリズムを必要とする場合）およびGLMNetフィッティングアルゴリズムの収束基準です。デフォルトは1e-5です。計算を高速化するために、より低い`tol`を設定することを試みることができます。収束はより速くなりますが、粗くなり、入力特徴の信号対ノイズ比に応じて分類精度が低下する可能性があります。

`verbose`がtrue（デフォルト）である場合、情報がREPLに印刷されます。

`⏩`引数（デフォルトでtrue）は、`𝐏Tr`内の行列を接線空間に射影するための[`tsMap`](@ref)関数および最適なモデルを見つけるための`GLMNet.glmnetcv`関数に渡され、マルチスレッドを使用して内部交差検証を実行します。

**参照**: [記法と命名法](@ref)、[ℍVector型](@ref)

**関連項目**: [`predict`](@ref)、[`crval`](@ref)

**チュートリアル**: [ENLRモデルを使用した例](@ref)

**例**

```julia
using PosDefManifoldML, PosDefManifold

# データを生成
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.1)

# ENLRラッソモデルをフィットさせ、交差検証で最適なモデルを見つける
m = fit(ENLR(), PTr, yTr)

# ... 接線ベクトルを標準化
m = fit(ENLR(), PTr, yTr; pipeline=p, normalize=standardize!)

# ... 接線空間マッピングのための重みをバランスさせる
m = fit(ENLR(), PTr, yTr; w=tsWeights(yTr))

# ... 接線空間射影のために対数ユークリッドメトリックを使用
m = fit(ENLR(logEuclidean), PTr, yTr)

# ENLRリッジモデルをフィットさせ、交差検証で最適なモデルを見つける：
m = fit(ENLR(Fisher), PTr, yTr; alpha=0)

# ENLR弾性ネットモデル（α=0.9）をフィットさせ、交差検証で最適なモデルを見つける：
m = fit(ENLR(Fisher), PTr, yTr; alpha=0.9)

# ENLRラッソモデルをフィットさせ、その正則化パスを取得：
m = fit(ENLR(), PTr, yTr; fitType=:path)

# ENLRラッソモデルをフィットさせ、その正則化パスと
# 交差検証で見つけた最適なモデルを取得：
m = fit(ENLR(), PTr, yTr; fitType=:all)

# 前処理パイプラインを使用してフィット：
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
m = fit(ENLR(PosDefManifold.Euclidean), PTr, yTr; pipeline=p)

# 再中心化パイプラインを使用し、データを
# アイデンティティ行列で接線空間に射影します。
# この場合、メトリックは無関係です。バリセンター
# の計算は行われません。
# 前の'fit'呼び出しが`PTr`を変更したため、
# 新しいデータを生成します。
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.1)
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
m = fit(ENLR(), PTr, yTr; pipeline=p, meanISR=I)
```
