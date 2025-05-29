```julia
    logdet0Mean(𝐏::Union{ℍVector, 𝔻Vector};
    <
    w::Vector=[],
    ✓w=true,
    init=nothing,
    tol::Real=0.,
    maxiter::Int=500,
    verbose=false,
    ⏩=true >)
```

**エイリアス**: `ld0Mean`

1次元配列 $𝐏={P_1,...,P_k}$ の $k$ 個の正定値行列（[ℍVector type](@ref) または実正定値対角行列の [𝔻Vector type](@ref)）とオプションの非負実重みベクトル $w={w_1,...,w_k}$ を与えると、3つのタプル $(G, iter, conv)$ を返します。ここで、$G$ は [logdet zero](@ref) メトリックに従った平均であり、$iter$ と $conv$ はアルゴリズムによって達成された反復回数と収束です。平均 $G$ は次の条件を満たす唯一の正定値行列です。

$$
\sum_{i=1}^{k}w_i\big(\frac{1}{2}P_i+\frac{1}{2}G\big)^{-1}-G^{-1}=0
$$

。

これを推定するために、この関数は (Moakher, 2012, p315)[🎓](@ref) によって提案された不動点反復アルゴリズムを実装しており、反復は次のようになります。

$$
G ← \frac{1}{2}\big(\sum_{i=1}^{k}w_i(P_i+G)^{-1}\big)^{-1}
$$

。

*<オプションのキーワード引数>* $w$ で重みベクトルを渡さない場合、*重みなしの logdet zero 平均* を返します。

*<オプションのキーワード引数>* `✓w=true`（デフォルト）の場合、重みは合計が1になるように正規化されます。そうでない場合は、渡された通りに使用され、すでに正規化されている必要があります。このオプションは、同じ重みベクトルを毎回正規化することなく、この関数を繰り返し呼び出すことを可能にするために提供されています。

以下はさらに多くの *<オプションのキーワード引数*> です：

  * `init` は平均の初期化に使用される行列です。行列が提供されない場合、[ユークリッド](@ref) 平均が使用されます。
  * `tol` は収束の許容誤差です（以下を参照）。
  * `maxiter` は許可される最大反復回数です。
  * `verbose`=true の場合、各反復で達成された収束が印刷され、収束が達成されなかった場合は *警告* が印刷されます。
  * ⏩=true の場合、反復はマルチスレッドで実行されます（以下を参照）。

!!! note "Nota Bene"
    [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) は、Julia が1つのスレッドのみを使用するように指示されている場合、自動的に無効になります。 [Threads](@ref) を参照してください。

    通常の状況では、このアルゴリズムは単調に収束します。アルゴリズムが発散し、`verbose` が true の場合、これが発生した反復を示す **警告** が印刷されます。


$$
tol
$$

は、データ入力 $𝐏$ の最も近い実数型の `Base.eps` の平方根の100倍にデフォルト設定されています。これは、2回の連続した反復にわたる相対収束基準の平方根が約半分の有効数字から2を引いた値で消失することを要求することに相当します。

**参照**: [logdet zero](@ref) メトリック、[修正されたバッタチャリヤ平均](@ref)。

**関連**: [`powerMean`](@ref)、[`wasMean`](@ref)、[`logdet0Mean`](@ref)、[`mean`](@ref)。

**例**

```julia
using LinearAlgebra, PosDefManifold
# 4つのランダムな3x3 SPD行列のセットを生成
Pset=randP(3, 4) # または、ユニコードを使用して: 𝐏=randP(3, 4)

# 重みなしの平均
G, iter, conv = logdet0Mean(Pset) # または G, iter, conv = logdet0Mean(𝐏)

# 重みベクトル、正規化する必要はありません
weights=[1, 2, 3, 1]

# 重み付き平均
G, iter, conv = logdet0Mean(Pset, w=weights)

# すべての反復での収束を印刷
G, iter, conv = logdet0Mean(Pset; w=weights, verbose=true)

# Pset が少し変更されたと仮定; G で初期化して収束を早める
Pset[1]=ℍ(Pset[1]+(randP(3)/100))
G, iter, conv = logdet0Mean(Pset; w=weights, ✓w=false, verbose=true, init=G)

# マルチスレッドモードでアルゴリズムを実行することで得られる利点を推定
using BenchmarkTools
Pset=randP(20, 120)
@benchmark(logdet0Mean(Pset; ⏩=false)) # シングルスレッド
@benchmark(logdet0Mean(Pset)) # マルチスレッド
```
