```julia
function fit(model :: MDMmodel,
              𝐏Tr   :: ℍVector,
              yTr   :: IntVector;
        pipeline :: Union{Pipeline, Nothing} = nothing,
        w        :: Vector = [],
        ✓w       :: Bool  = true,
        meanInit :: Union{ℍVector, Nothing} = nothing,
        tol      :: Real  = 1e-5,
        verbose  :: Bool  = true,
        ⏩       :: Bool  = true)
```

[`MDM`](@ref) 機械学習モデルを、トレーニングデータ `𝐏Tr`（型 [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1)）と対応するラベル `yTr`（型 [IntVector](@ref)）を使用してフィットします。フィットされたモデルを返します。

!!! warning "クラスラベル"
    ラベルは自然数を使用して提供する必要があります。すなわち、最初のクラスには `1`、2番目のクラスには `2`、などです。


MDMモデルのフィッティングは、各クラスのすべての行列の平均（バリセンター）を計算することだけを含みます。これらのクラス平均は、[`MDM`](@ref) コンストラクタによって指定されたメトリックに従って計算されます。

**オプションのキーワード引数：**

`pipeline`（型 [`Pipeline`](@ref)）が提供されると、条件付けのシーケンスのすべての必要なパラメータがフィットされ、すべての行列がフィットする前に指定されたパイプラインに従って変換されます。パラメータは出力MLモデルに保存されます。フィットされたパイプラインは、出力MLモデルが引数として渡される関数 [`predict`](@ref) への後続の呼び出しによって自動的に適用されることに注意してください。

`w` は、`𝐏Tr` の行列に関連付けられた非負の重みのベクトルです。これらの重みは、各クラスの平均を計算するために使用されます。引数 `w`、`✓w`、および `⏩` の意味については、[mean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Statistics.mean) 関数のメソッド (3) を参照してください。ここで、重みは各クラスごとに1に合計される必要があることを念頭に置いてください。これは、`✓w` が true の場合にこの関数によって保証されます。

`tol` は、平均を反復的に計算するアルゴリズムに必要な許容誤差です（それらはFisher、logdet0、またはWassersteinメトリックを採用しています）。デフォルトは 1e-5 です。この引数の詳細については、平均を計算するために呼び出される関数（*PosDefManifold.jl* パッケージから）を参照してください：

  * Fisherメトリック: [gmean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.geometricMean)
  * logdet0メトリック: [ld0mean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.logdet0Mean)
  * Wassersteinメトリック: [Wasmean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.wasMean).

これらのアルゴリズムには、オプションのキーワード引数 `meanInit` で初期化を提供できます。提供される場合、これは [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%F0%9D%95%84Vector-type-1) 型の `Hermitian` 行列のベクトルであり、クラスラベルに対応する自然な順序でクラスの数だけ初期化を含む必要があります（上記参照）。

`verbose` が true の場合（デフォルト）、情報が REPL に出力されます。

**参照**: [記法と命名法](@ref)、[ℍVector型](@ref)

**関連項目**: [`predict`](@ref)、[`crval`](@ref)

**例**

```julia
using PosDefManifoldML, PosDefManifold

# データを生成する
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80, 0.25)

# モデルを作成してフィットさせる:
m = fit(MDM(Fisher), PTr, yTr)

# 前処理パイプラインを使用してモデルを作成してフィットさせる:
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
m = fit(MDM(Fisher), PTr, yTr; pipeline=p)
```
