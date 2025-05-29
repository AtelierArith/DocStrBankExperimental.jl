```julia
mutable struct Recenter <: Conditioner
    metric 
    eVar 
    w 
    ✓w 
    init 
    tol 
    verbose 
    forcediag 
    threaded 
    ## Fitted parameters
    Z 
    iZ 
```

**再中心化**コンディショナーのための可変構造体。

正定値行列のマニフォールドにおける `n·n` 点の集合 $𝐏$ が与えられたとき、次のように集合を変換します。

$$
ZP_jZ^T, \ j=1,...,k
$$

,

ここで $Z$ はコンディショナーによって指定された $𝐏$ のバリセンターのホワイトニング行列です。すなわち、$G$ が $𝐏$ のバリセンターである場合、$ZGZ^T=I$ となります。

再中心化の後、バリセンターは単位行列になり、ホワイトニングされた行列の固有値の平均は 1 になります。正定値行列のマニフォールドにおいて、再中心化はすべての点を単位バリセンターに平行輸送することに相当します。

[`Recenter`](@ref) コンディショナーを定義するために使用される `eVar` 値に応じて、行列 $Z$ は入力点の次元削減を決定する場合もあります。この場合、$Z$ は正方行列ではなく、次元 $p·n$ のワイド行列であり、$p<n$ です。

このコンディショナーは **教師あり** の方法で動作する場合があります。フィッティング時にクラスラベルを提供すると（[`fit!`](@ref) を参照）、クラスはバリセンター $G$ を計算するために等しく重み付けされます。これは、接空間マッピングに使用されるバリセンターを計算するための [`tsWeights`](@ref) と同様です。クラスがバランスしている場合、重み付けは影響を与えません。

このコンディショナー構造体には次のフィールドがあります：

  * `.metric` は、ユーザーによって指定される [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1) 型です。クラスの平均と平均への距離を計算するために採用されるメトリックです。デフォルトは `PosDefManifold.Euclidean` です。
  * `.eVar` は、ホワイトニングのための希望する説明された分散です。Real、Int、または `nothing` であることができます。Diagonalizations.jl のメソッド [whitening](https://marco-congedo.github.io/Diagonalizations.jl/dev/whitening/#Diagonalizations.whitening) のドキュメントを参照してください。デフォルトは 0.9999 です。
  * フィールド `.w`、`.✓w`、`.init`、および `.tol` は、バリセンター $G$ を計算するために PosDefManifold.jl の [mean](https://marco-congedo.github.io/PosDefManifold.jl/latest/riemannianGeometry/#Statistics.mean) メソッドに渡されます。詳細については、そこにあるドキュメントを参照してください。
  * `.verbose` は、`fit!` および `transform!` を使用する際に REPL に情報を印刷するかどうかを決定するブール値です。デフォルトは false です。
  * `.forcediag` は、対角化を強制するためのブール値です。デフォルトは true です。false の場合、ホワイトニングは次元削減が必要な場合にのみ実行されます。これは `eVar` によって決定されます。
  * `.threaded` が true の場合（デフォルト）、すべての操作はマルチスレッドで実行されます。

インスタンスを構築するために、`metric` は引数であり、`eVar`、`w`、`✓w`、`init`、`tol`、`verbose`、`forcediag`、および `threaded` はオプションのキーワード引数です。

**フィッティングされたパラメータ**

コンディショナーがフィッティングされると、次のフィールドが書き込まれます：

  * `.Z` は、フィッティングされたセット $P_j, \ j=1,...,k$ のホワイトニング行列であり、$ZP_jZ^T$ がホワイトニングされます。
  * `.iZ` は、$Z$ の左逆行列 $Z^*$ であり、次元削減が行われない場合、$Z^*Z=I$（単位行列）となります。

次元削減が行われる場合、$Z^*Z≠I$ はランク $p$ になります。

**例**：

```julia
using PosDefManifoldML, PosDefManifold

# デフォルトのコンディショナーを作成
R = Recenter(PosDefManifold.Euclidean)

# ユークリッドメトリックがデフォルトメトリックであるため、
# これは次のように等価です
R = Recenter()

# 次元削減を行わない
R = Recenter(PosDefManifold.Fisher; eVar=nothing)

# 次元を 10 に削減
R = Recenter(PosDefManifold.Fisher; eVar=10)

# 分散の少なくとも 90% を説明する次元を決定
R = Recenter(PosDefManifold.Fisher; eVar=0.9)

# クラスラベルを使用してクラス間の重みをバランスさせる
# （`y` がクラスラベルを保持する整数のベクターであるとします）
R = Recenter(PosDefManifold.Fisher; labels=y)

```

**関連項目**: [`fit!`](@ref), [`transform!`](@ref), [`crval`](@ref)
