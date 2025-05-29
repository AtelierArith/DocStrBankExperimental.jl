```julia
mutable struct SVM <: SVMmodel
	metric		:: Metric
	svmType		:: Type
	kernel		:: Kernel.KERNEL
	pipeline 	:: Pipeline
	normalize	:: Union{Function, Tuple, Nothing}
	meanISR		:: Union{HermitianVector, Nothing, UniformScaling}
	vecRange	:: UnitRange
	featDim		:: Int
	svmModel #store the training model from the SVM library
```

SVM機械学習モデルは、この可変構造体にカプセル化されています。フィールド：

`.metric`は、[Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1)型で、接空間投影の基準点として使用される平均を計算するために採用されるメトリックです。デフォルトではフィッシャーメトリックが採用されます。利用可能なメトリックについては、[mdm.jl](@ref)を参照してください。モデルのトレーニングに使用されるデータが正定値行列ではなく、ユークリッド特徴ベクトルである場合、`.metric`フィールドは無用です。メトリックを使用するには、*PosDefManifold*パッケージをインストールする必要があります。

`svmType`は、LIBSVMで使用されるSVMモデルの一般的な型です。利用可能なタイプは次のとおりです：

  * `SVC`: *C-サポートベクター分類*。フィット時間の複雑さは観測数に対して二次以上です。マルチクラスサポートは一対一のスキームに従って処理されます。
  * `NuSVC`: *Nu-サポートベクター分類*。SVCに似ていますが、サポートベクターの数を制御するパラメータを使用します。
  * `OneClassSVM`: 教師なし外れ値検出。高次元分布のサポートを推定します。
  * `EpsilonSVR`: *Epsilon-サポートベクター回帰*。
  * `NuSVR`: *Nu-サポートベクター回帰*。

デフォルトは`SVC`ですが、モデルをフィッティングする際にラベルが提供されない場合は、`OneClassSVM`にデフォルト設定されます。

`kernel`はカーネルタイプです。利用可能なカーネルは、メインモジュールで定数として宣言されています。これらは次のとおりです：

  * `Linear` 		(デフォルト)
  * `RadialBasis`
  * `Polynomial`
  * `Sigmoid`
  * `Precomputed` (サポートされていません)。

他のすべてのフィールドは、デフォルトの作成者によってモデルの作成時に渡される引数に対応していません。代わりに、モデルが[`fit`](@ref)関数によって作成されるときに後で埋められます：

フィールド`vecRange`と`normalize`の内容については、ENLRモデルの[`fit`](@ref)関数のドキュメントを参照してください。

`.meanISR`、`.featDim`、および`pipeline`フィールドの内容については、[`ENLR`](@ref)構造体のドキュメントを参照してください。

`svmModel`は、モデルがフィットされたときにLIBSVMによって作成されたモデル構造を保持します（[ここ](https://github.com/mpastell/LIBSVM.jl/blob/master/src/LibSVMtypes.jl)で宣言されています）。

**例**：

```julia
# 注意: デフォルトの作成者を使用してモデルを作成することは可能ですが、
# 一般的には有用ではありません。

using PosDefManifoldML, PosDefManifold

# 空のSVMモデルを作成
m = SVM(Fisher)

# フィッシャーメトリックがデフォルトメトリックであるため、
# これは次と同等です
m = SVM()

# logEuclideanメトリックを使用して空のSVMモデルを作成
m = SVM(logEuclidean)

# データを生成
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.1);

# 空のモデルは`fit`関数の最初の引数として渡すことができ、
# モデルをフィットさせます。たとえば、これは`m`と同じ種類の
# SVMモデルをフィットさせ、フィットしたモデルを`m1`に置きます：
m1 = fit(m, PTr, yTr)

# 一般的に、モデルをフィットさせるためにこの機構は必要ありません。
# なぜなら、即座にモデルを作成することでモデルを指定できるからです：
m2 = fit(SVM(logEuclidean), PTr, yTr; kernel=Linear)

# これは次と同等です
m2 = fit(m, PTr, yTr; kernel=Linear)

# モデル`m`がデフォルトカーネル（RadialBasis）を持つSVMモデルとして作成されたにもかかわらず、
# `m`を渡して`kernel`タイプを上書きしました。
# `svmType`も上書きできます。
# ただし、メトリックは上書きできません。
```
