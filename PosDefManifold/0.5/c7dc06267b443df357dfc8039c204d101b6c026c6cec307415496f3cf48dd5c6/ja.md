```julia
    geometricMean(𝐏::Union{ℍVector, 𝔻Vector};
    <
    w::Vector=[],
    ✓w=true,
    init=nothing,
    tol::Real=0.,
    maxiter::Int=200,
    adaptStepSize::Bool=true,
    verbose=false,
    ⏩=true >)
```

**エイリアス**: `gMean`

1次元配列 $𝐏={P_1,...,P_k}$ の $k$ 個の正定値行列（[ℍVector type](@ref) または [𝔻Vector type](@ref) の対角行列）のオプションの非負実数重みベクトル $w={w_1,...,w_k}$ を与えると、3つのタプル $(G, iter, conv)$ を返します。ここで、$G$ は [Fisher](@ref) メトリックに従った平均であり、$iter$ と $conv$ はアルゴリズムによって達成された反復回数と収束を示します。平均 $G$ は次の条件を満たす唯一の正定値行列です。

$$
\sum_{i=1}^{k}w_i\textrm{log}\big(G^{-1/2} P_i G^{-1/2}\big)=0.
$$

これを推定するために、この関数はよく知られた勾配降下アルゴリズムを実装していますが、指数的に減衰するステップサイズ $ς$ を使用し、反復は次のようになります。

$$
G ← G^{1/2}\textrm{exp}\big(ς\sum_{i=1}^{k}w_i\textrm{log}(G^{-1/2} P_i G^{-1/2})\big)G^{1/2}.
$$

*<オプションのキーワード引数>* $w$ で重みベクトルを渡さない場合、*重みなしの幾何平均*を返します。

*<オプションのキーワード引数>* `✓w=true`（デフォルト）の場合、重みは合計が1になるように正規化されます。そうでない場合は、渡された通りに使用され、すでに正規化されている必要があります。このオプションは、同じ重みベクトルを毎回正規化することなく、この関数を繰り返し呼び出すことを可能にするために提供されています。

以下はさらに多くの *<オプションのキーワード引数*> です：

  * `init` は平均の初期化に使用される行列です。行列が提供されない場合、[ユークリッド](@ref) 平均が使用されます。
  * `tol` は収束の許容誤差です（以下を参照）。
  * `maxiter` は許可される最大反復回数です。
  * `verbose`=true の場合、各反復で達成された収束とステップサイズ $ς$ が印刷されます。また、収束が達成されない場合は*警告*が印刷されます。
  * ⏩=true の場合、反復はマルチスレッドで実行されます（以下を参照）。
  * `adaptStepSize`=false の場合、ステップサイズ `ς` はすべての反復で1に固定されます。

入力が $k$ 個の実正定値対角行列の1次元配列である場合、解は対数ユークリッド平均として閉じた形で利用可能です。したがって、*<オプションのキーワード引数*> `init`、`tol`、および `verbose` は効果がなく、3つのタプル $(G, 1, 0)$ を返します。 [対数ユークリッド](@ref) メトリックを参照してください。

!!! note "Nota Bene"
    [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) は、Julia が1つのスレッドのみを使用するように指示された場合、自動的に無効になります。[Threads](@ref) を参照してください。

    通常の状況では、このアルゴリズムは単調に収束します。アルゴリズムが発散し、`verbose` が true の場合、発生した反復を示す**警告**が印刷されます。

    指数的に減衰するステップサイズは、通常採用される固定ステップサイズ $ς=1$ と比較して、より速い収束率を特徴とします。減衰率は `maxiter` に反比例するため、遅い/速い減衰率を設定するために `maxiter` を増減させてください。ただし、`maxiter` はあまり低く設定しないでください。

    $$
    tol
    $$

    は、入力データ $𝐏$ の最も近い実数型の `Base.eps` の平方根にデフォルト設定されます。これは、満たす行列方程式のノルムを要素数で割ったものが約半分の有効数字で消失することを要求することに相当します。


**参照**: [Fisher](@ref) メトリック。

**関連**: [`geometricpMean`](@ref)、[`powerMean`](@ref)、[`wasMean`](@ref)、[`logdet0Mean`](@ref)、[`mean`](@ref)。

**例**

```julia
using LinearAlgebra, PosDefManifold
# 4つのランダムな3x3 SPD行列のセットを生成
Pset=randP(3, 4) # または、ユニコードを使用して: 𝐏=randP(3, 4)

# 重みなしの平均
G, iter, conv = geometricMean(Pset) # または G, iter, conv = geometricMean(𝐏)

# 重みベクトル、正規化する必要はありません
weights=[1, 2, 3, 1]

# 重み付き平均
G, iter, conv = geometricMean(Pset, w=weights)

# すべての反復で収束を印刷
G, iter, conv = geometricMean(Pset; verbose=true)

# さて、Psetが少し変わったと仮定し、Gで初期化して収束を早めます
Pset[1]=ℍ(Pset[1]+(randP(3)/100))
G, iter, conv = geometricMean(Pset; w=weights, ✓w=true, verbose=true, init=G)

# 行列の数が多い場合はマルチスレッドで実行
using BenchmarkTools
Pset=randP(20, 120)
@benchmark(geometricMean(Pset; ⏩=false)) # シングルスレッド
@benchmark(geometricMean(Pset)) # マルチスレッド

# スペクトル埋め込みを使用して平均と入力点を表示
using Plots
k=80
Pset=randP(20, k)
G, iter, conv = geometricMean(Pset)
push!(Pset, G)
Λ, U, iter, conv=spectralEmbedding(Fisher, Pset, 2; verbose=true)
plot(U[1:k, 1], U[1:k, 2], seriestype=:scatter, title="スペクトル埋め込み", label="Pset")
plot!(U[k+1:k+1, 1], U[k+1:k+1, 2], seriestype=:scatter, label="平均")
```
