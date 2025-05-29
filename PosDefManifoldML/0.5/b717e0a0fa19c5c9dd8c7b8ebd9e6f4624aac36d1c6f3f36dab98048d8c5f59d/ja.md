```julia
function fit(model     :: SVMmodel,
               𝐏Tr     :: Union{HermitianVector, Matrix{Float64}},
               yTr     :: IntVector=[];

	# パイプライン（データ変換）
	pipeline    :: Union{Pipeline, Nothing} = nothing,

	# 接空間への射影のためのパラメータ
	w		:: Union{Symbol, Tuple, Vector} = Float64[],
	meanISR 	:: Union{Hermitian, Nothing, UniformScaling} = nothing,
	meanInit 	:: Union{Hermitian, Nothing} = nothing,
	vecRange	:: UnitRange = 𝐏Tr isa HermitianVector ? (1:size(𝐏Tr[1], 2)) : (1:size(𝐏Tr, 2)),
	normalize	:: Union{Function, Tuple, Nothing} = normalize!,

	# SVMパラメータ
	svmType 	:: Type = SVC,
	kernel 		:: Kernel.KERNEL = Linear,
	epsilon 	:: Float64 = 0.1,
	cost		:: Float64 = 1.0,
	gamma 		:: Float64	= 1/_getDim(𝐏Tr, vecRange),
	degree 		:: Int64	= 3,
	coef0 		:: Float64	= 0.,
	nu 			:: Float64 = 0.5,
	shrinking 	:: Bool = true,
	probability	:: Bool = false,
	weights 	:: Union{Dict{Int, Float64}, Nothing} = nothing,
	cachesize 	:: Float64	= 200.0,
	checkArgs	:: Bool = true,

	# 一般的かつ共通のパラメータ
	tol		:: Real = 1e-5,
	verbose		:: Bool = true,
	⏩		:: Bool = true)
```

**1クラス**または**2クラス**のサポートベクターマシン（[`SVM`](@ref)）機械学習モデルを作成し、トレーニングデータ`𝐏Tr`（タイプ[ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1)）と対応するラベル`yTr`（タイプ[IntVector](@ref)）を使用してフィットさせます。ラベルベクトルは、`svmType`が`OneClassSVM`の場合は省略できます（[`SVM`](@ref)を参照）。フィットしたモデルは、[`SVM`](@ref)構造のインスタンスとして返されます。

!!! warning "クラスラベル"
    ラベルは自然数を使用して提供する必要があります。すなわち、最初のクラスには`1`、2番目のクラスには`2`などです。


接空間で動作するすべてのMLモデルと同様に、SVMモデルのフィッティングには、`𝐏Tr`内のすべての行列の平均（重心）を計算し、すべての行列をアイデンティティ行列で平行移動した後に接空間に射影し、[vecP](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.vecP)操作を使用してベクトル化することが含まれます。これが完了すると、サポートベクターマシンがフィットされます。

**オプションのキーワード引数**

以下のキーワード引数については、ENLR（Elastic Net Logistic Regression）機械学習モデルの[`fit`](@ref)関数のドキュメントを参照してください：

  * `pipeline`（前処理）、
  * `w`、`meanISR`、`meanInit`、`vecRange`（接空間射影）、

!!! tip "ユークリッドSVMモデル"
    接空間で動作するMLモデルは、トレーニングデータ`𝐏Tr`として特徴ベクトルの行列を直接渡すことでモデルをフィットさせることができます。この場合、上記のキーワード引数は使用されません。


  * `normalize`（接空間または特徴ベクトルの正規化）。

**LIBSVM.jlを使用してモデルをフィットさせるためのオプションのキーワード引数**

`svmType`と`kernel`は、利用可能な複数のSVMモデルの中から選択することを可能にします。[`SVM`](@ref)構造のドキュメントを参照してください。

`epsilon`はデフォルトで0.1で、`epsilonSVR` SVMモデルの損失関数のεです。

`cost`はデフォルトで1.0で、`SVC`、`epsilonSVR`、および`nuSVR` SVMモデルのコストパラメータ*C*です。

`gamma`はデフォルトで接空間（または特徴）ベクトルの長さの逆数で、`RadialBasis`、`Polynomial`、および`Sigmoid`カーネルの*γ*パラメータです。提供された引数`gamma`は、前処理`pipeline`が引数として渡され、パイプラインが入力行列の次元を変更する場合は無視されます。この場合、新しい次元を使用してデフォルト値に設定されます。提供された`gamma`値を強制的に使用するには、`checkArgs`をfalseに設定します（デフォルトはtrueです）。

`degree`はデフォルトで3で、`Polynomial`カーネルの次数です。

`coef0`はデフォルトでゼロで、`Sigmoid`および`Polynomial`カーネルのパラメータです。

`nu`はデフォルトで0.5で、`nuSVC`、`OneClassSVM`、および`nuSVR` SVMモデルのパラメータ*ν*です。これは(0, 1]の範囲内である必要があります。

`shrinking`はデフォルトでtrueで、シュリンクヒューリスティックを使用するかどうかを設定します。

`probability`はデフォルトでfalseで、確率推定を許可する`SVC`または`SVR`モデルをトレーニングするかどうかを設定します。

`Dict{Int, Float64}`が`weights`引数として渡されると、それはクラスに重みを与えるために使用されます。デフォルトでは`nothing`と等しく、すべてのクラスに等しい重みを意味します。

`cachesize`はカーネルのために200.0（MB単位）でデフォルトであり、非常に大きな問題に対して増加させることができます。

`tol`は、接空間への射影のための平均を計算する際の収束基準（メトリックが反復アルゴリズムを必要とする場合）およびLIBSVMフィッティングアルゴリズムの収束基準です。デフォルトは1e-5です。

`verbose`がtrueの場合（デフォルト）、REPLに情報が印刷されます。このオプションは、REPLを混雑させずにこの関数を繰り返し呼び出すことを可能にするために含まれています。

`⏩`引数（デフォルトでtrue）は、`𝐏Tr`内の行列を接空間に射影するための[`tsMap`](@ref)関数およびフィットを実行するLIBSVM関数に渡され、マルチスレッドモードで実行されます。

LIBSVM引数に関する詳細情報については、LIBSVMパッケージのリソースを参照してください[🎓](@ref)。

**参照**: [表記法と命名法](@ref)、[ℍVector型](@ref)

**関連**: [`predict`](@ref)、[`crval`](@ref)

**チュートリアル**: [SVMモデルを使用した例](@ref)

**例**

```julia
using PosDefManifoldML, PosDefManifold

# データを生成
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.1);

# SVC SVMモデルをフィットさせ、交差検証によって最良のモデルを見つける：
m = fit(SVM(), PTr, yTr)

# ... 接空間マッピングのために重みをバランスさせる
m = fit(SVM(), PTr, yTr; w=:b)

# ... 接空間射影のために対数ユークリッドメトリックを使用
m = fit(SVM(logEuclidean), PTr, yTr)

# ... 線形カーネルを使用
m = fit(SVM(logEuclidean), PTr, yTr, kernel=Linear)

# または

m = fit(SVM(logEuclidean; kernel=Linear), PTr, yTr)

# ... Nuサポートベクタ分類を使用
m = fit(SVM(logEuclidean), PTr, yTr, kernel=Linear, svmtype=NuSVC)

# または

m = fit(SVM(logEuclidean; kernel=Linear, svmtype=NuSVC), PTr, yTr)

# N.B. 他のすべてのキーワード引数はfit関数に渡す必要があり、
# SVMコンストラクタには渡さないでください。

# 前処理パイプラインを使用してSVC SVMモデルをフィットさせる：
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
m = fit(SVM(PosDefManifold.Euclidean), PTr, yTr; pipeline=p)

# 再中心化パイプラインを使用し、データを
# アイデンティティ行列での接空間に射影します。
# この場合、基準点を決定するための重心は計算されないため、
# メトリックは無関係です。
# 前の'fit'呼び出しが`PTr`を変更したため、
# 新しいデータを生成します。
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.1)
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
m = fit(SVM(), PTr, yTr; pipeline=p, meanISR=I)
```
