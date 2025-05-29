```julia
    wasMean(𝐏::Union{ℍVector, 𝔻Vector};
    <
    w::Vector=[],
    ✓w=true,
    init=nothing,
    tol::Real=0.,
    maxiter::Int=500,
    verbose=false,
    ⏩=true >)
```

与えられた1次元配列 $𝐏={P_1,...,P_k}$ は、[ℍVector type](@ref) の $k$ 個の正定値行列または [𝔻Vector type](@ref) の実正定値対角行列のオプションの非負実重みベクトル $w={w_1,...,w_k}$ を持ち、3タプル $(G, iter, conv)$ を返します。ここで、$G$ は [Wasserstein](@ref) メトリックに従った平均であり、$iter$ と $conv$ はアルゴリズムによって達成された反復回数と収束です。平均 $G$ は次の条件を満たす唯一の正定値行列です。

$$
G=\sum_{i=1}^{k}w_i\big( G^{1/2}  P_i G^{1/2}\big)^{1/2}
$$

。

これを推定するために、この関数は (Álvarez-Esteban et *al.*, 2016)[🎓](@ref) によって提案された不動点反復アルゴリズムを実装しています：

$$
G ← G^{-1/2}\big(\sum_{i=1}^{k} w_i(G^{1/2}P_i G^{1/2})^{1/2}\big)^2 G^{-1/2}
$$

。

*<optional keyword argument>* $w$ で重みベクトルを渡さない場合、*非加重Wasserstein平均*を返します。

*<optional keyword argument>* `✓w=true` (デフォルト) の場合、重みは合計が1になるように正規化されます。そうでない場合は、渡された通りに使用され、すでに正規化されている必要があります。このオプションは、同じ重みベクトルを毎回正規化することなく、この関数を繰り返し呼び出すことを可能にするために提供されています。

以下は、さらに多くの *<optional keyword arguments*> です：

  * `init` は平均の初期化に使用される行列です。行列が提供されない場合、$p=0.5$ の [generalized means](@ref) のインスタンスが使用されます。
  * `tol` は収束の許容誤差です (以下を参照)。
  * `maxiter` は許可される最大反復回数です。
  * `verbose`=true の場合、各反復で達成された収束が印刷され、収束が達成されなかった場合は *警告* が印刷されます。
  * ⏩=true の場合、反復はマルチスレッドで実行されます (以下を参照)。

入力が $k$ 個の実正定値対角行列の1次元配列である場合、解は修正バッタチャリヤ平均として閉じた形で利用可能です。したがって、*<optional keyword arguments*> `init`、`tol`、および `verbose` は効果がなく、3タプル $(G, 1, 0)$ を返します。詳細は [modified Bhattacharyya mean](@ref) を参照してください。

!!! note "Nota Bene"
    [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) は、Julia が1つのスレッドのみを使用するように指示されている場合、自動的に無効になります。詳細は [Threads](@ref) を参照してください。

    通常の状況では、このアルゴリズムは単調に収束します。アルゴリズムが発散した場合、`verbose` が true の場合は、これが発生した反復を示す **警告** が印刷されます。

    $$
    tol
    $$

    は、入力データ $𝐏$ の最も近い実数型の `Base.eps` の平方根にデフォルト設定されています。これは、満たす行列方程式のノルムを要素数で割ったものが約半分の有効数字で消失することを要求することに対応します。


**参照**: [Wasserstein](@ref) メトリック。

**関連**: [`powerMean`](@ref), [`wasMean`](@ref), [`logdet0Mean`](@ref), [`mean`](@ref)。

**例**

```julia
using LinearAlgebra, PosDefManifold
# 4つのランダムな3x3 SPD行列のセットを生成
Pset=randP(3, 4) # または、ユニコードを使用して: 𝐏=randP(3, 4)

# 非加重平均
G, iter, conv = wasMean(Pset) # または: G, iter, conv = wasMean(𝐏)

# 重みベクトル、正規化する必要はありません
weights=[1, 2, 3, 1]

# 加重平均
G, iter, conv = wasMean(Pset; w=weights)

# すべての反復での収束を印刷
G, iter, conv = wasMean(Pset; w=weights, verbose=true)

# 𝐏 が少し変更されたと仮定; 収束を早めるために G で初期化
Pset[1]=ℍ(Pset[1]+(randP(3)/100))
G, iter, conv = wasMean(Pset; w=weights, verbose=true, init=G)

# マルチスレッドモードでアルゴリズムを実行することで得られる利得を推定
using BenchmarkTools
Pset=randP(20, 120)
@benchmark(wasMean(Pset; ⏩=false)) # シングルスレッド
@benchmark(wasMean(Pset)) # マルチスレッド
```
