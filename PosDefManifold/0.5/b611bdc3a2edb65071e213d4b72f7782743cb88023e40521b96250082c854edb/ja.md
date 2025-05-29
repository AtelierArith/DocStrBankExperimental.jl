```julia
    powerMean(𝐏::Union{ℍVector, 𝔻Vector}, p::Real;
    <
    w::Vector=[],
    ✓w=true,
    init=nothing,
    tol::Real=0.,
    maxiter::Int=500,
    verbose=false,
    ⏩=true >)
```

正定行列の1d配列$𝐏={P_1,...,P_k}$（[ℍVector type](@ref)または実正定対角行列の[𝔻Vector type](@ref））と、オプションの非負実重みベクトル$w={w_1,...,w_k}$、および実数パラメータ`p` $\in[-1, 1]$を与えると、3つのタプル$(G, iter, conv)$を返します。ここで、$G$はLimとPalfia（2012）の[power means](@ref)で、順序は$p$であり、$iter$と$conv$はそれぞれアルゴリズムによって達成された反復回数と収束を示します。平均$G$は、次の条件を満たす一意の正定行列です。

$$
G=\sum_{i=1}^{k}w_i(G\textrm{#}_pP_i)
$$

、

ここで、$G\textrm{#}_pP_i$は[Fisher](@ref)の[geodesic](@ref)方程式です。特に：

  * $$
    p=-1
    $$

    の場合、これは*調和平均*です（[逆ユークリッド](@ref)距離を参照）。
  * $$
    p=+1
    $$

    の場合、これは*算術平均*です（[ユークリッド](@ref)距離を参照）。
  * $$
    p
    $$

    が両側からゼロで評価される限界では、これは*幾何平均*です（[Fisher](@ref)距離を参照）。

$$
p\in(-1, 1)
$$

のためのpower meansを推定するために、この関数は(Congedo et *al.*, 2017b)[🎓](@ref)の固定点反復アルゴリズムを実装しています。$p=0$（幾何平均）の場合、このアルゴリズムは$p$の小さな正の値と負の値で2回実行され、2つの結果の平均の幾何平均が返されます。これは(Congedo et *al.*, 2017b)[🎓](@ref)で提案されています。この行列のセットの幾何平均を推定する方法は、通常の勾配降下アルゴリズムと比較して高速です。

*<オプションのキーワード引数>* $w$を渡さない場合、*重みなしのpower mean*を返します。

*<オプションのキーワード引数>* `✓w=true`（デフォルト）の場合、重みは1に合計されるように正規化されます。そうでない場合、渡された通りに使用され、すでに正規化されている必要があります。このオプションは、同じ重みベクトルを毎回正規化することなく、この関数を繰り返し呼び出すことを可能にします。

以下は、さらに*<オプションのキーワード引数*>です：

  * `init`は、平均の初期化に使用される行列です。行列が提供されていない場合、パラメータ$p$を持つ[一般化平均](@ref)のインスタンスが使用されます。
  * `tol`は収束の許容範囲です（以下を参照）。
  * `maxiter`は許可される最大反復回数です。
  * `verbose`=trueの場合、各反復で達成された収束が印刷され、収束が達成されなかった場合は*警告*が印刷されます。
  * ⏩=trueの場合、反復はマルチスレッドで実行されます。

入力が$k$の実正定対角行列の1d配列である場合、解は順序`p`の一般化平均として閉じた形で利用可能です。したがって、*<オプションのキーワード引数*> `init`、`tol`、および`verbose`は効果がなく、3つのタプル$(G, 1, 0)$を返します。[一般化平均](@ref)を参照してください。

!!! note "Nota Bene"
    [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1)は、Juliaが1つのスレッドのみを使用するように指示されている場合、自動的に無効になります。[Threads](@ref)を参照してください。

    通常の状況では、このアルゴリズムは単調に収束します。アルゴリズムが発散し、`verbose`がtrueの場合、発生した反復を示す**警告**が印刷されます。

    $$
    tol
    $$

    は、入力データ$𝐏$の最も近い実数型の`Base.eps`の平方根にデフォルト設定されています。これは、行列の解の差のノルムが2つの連続した反復で、行列の要素数で割った値が約半分の有効数字で消失することを要求することに対応します。


(2) (1)と同様ですが、$k$の実正定対角行列の1d配列$𝐃={D_1,...,D_k}$の場合です。この場合、解は閉じた形で利用可能であるため、*<オプションのキーワード引数*> `init`、`tol`、および`verbose`は効果がなく、3つのタプル$(G, 1, 0)$を返します。[一般化平均](@ref)を参照してください。

**参照**: [power means](@ref)、[一般化平均](@ref)、[修正バタチャリヤ平均](@ref)。

**関連**: [`generalizedMean`](@ref)、[`wasMean`](@ref)、[`logdet0Mean`](@ref)、[`mean`](@ref)。

**例**

```julia
using LinearAlgebra, PosDefManifold
# 4つのランダムな3x3 SPD行列のセットを生成
Pset=randP(3, 4) # または、ユニコードを使用して: 𝐏=randP(3, 4)

# 重みなしの平均
G, iter, conv = powerMean(Pset, 0.5) # または G, iter, conv = powerMean(𝐏, 0.5)

# 重みベクトル、正規化する必要はありません
weights=[1, 2, 3, 1]

# 重み付き平均
G, iter, conv = powerMean(Pset, 0.5; w=weights)

# すべての反復での収束を印刷
G, iter, conv = powerMean(Pset, 0.5; w=weights, verbose=true)

# 𝐏が少し変わったと仮定します; Gで初期化して収束を早めます
Pset[1]=ℍ(Pset[1]+(randP(3)/100))
G, iter, conv = powerMean(Pset, 0.5; w=weights, verbose=true, init=G)

# マルチスレッドモードでアルゴリズムを実行することで得られる利得を推定
using BenchmarkTools
Pset=randP(20, 120)
@benchmark(powerMean(Pset, 0.5; ⏩=false)) # シングルスレッド
@benchmark(powerMean(Pset, 0.5)) # マルチスレッド
```
