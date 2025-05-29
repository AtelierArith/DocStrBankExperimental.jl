```julia
    geometricpMean(𝐏::ℍVector, p::Real=0.5;
    <
    w::Vector=[],
    ✓w=true,
    init=nothing,
    tol::Real=0.,
    maxiter::Int=500,
    adaptStepSize=true,
    verbose=false,
    ⏩=true >)
```

**エイリアス**: `gpmean`

1次元配列 $𝐏={P_1,...,P_k}$ の $k$ 個の正定値行列 [ℍVector type](@ref)、実数パラメータ $0<p<=1$ およびオプションの非負実数重みベクトル $w={w_1,...,w_k}$ を与えると、3つのタプル $(G, iter, conv)$ を返します。ここで、$G$ は *p-平均* であり、すなわち *p-分散* を最小化する [Fisher](@ref) メトリックに従った平均であり、$iter$ と $conv$ はアルゴリズムによって達成された反復回数と収束を示します。

この関数は、ステップサイズ $ς$ を用いた p-分散勾配降下アルゴリズムを実装しており、反復を生成します。

$$
G ←G^{1/2}\textrm{exp}\big(ς\sum_{i=1}^{k}pδ^2(G, P_i)^{p-1}w_i\textrm{log}(G^{-1/2} P_i G^{-1/2})\big)G^{1/2}.
$$

  * $$
    p=1
    $$

    の場合、これは幾何平均を生成します（[`geometricMean`](@ref) で特に実装されています）。
  * $$
    p=0.5
    $$

    の場合、これは幾何中央値を生成します（デフォルト）。

*<オプションのキーワード引数>* $w$ で重みベクトルを渡さない場合、*重みなしの幾何-p 平均* を返します。

*<オプションのキーワード引数>* `✓w=true`（デフォルト）の場合、重みは合計が1になるように正規化されます。そうでない場合、渡された通りに使用され、すでに正規化されている必要があります。このオプションは、同じ重みベクトルを毎回正規化することなく、この関数を繰り返し呼び出すことを可能にするために提供されています。

以下はさらに多くの *<オプションのキーワード引数*> です：

  * `init` は平均の初期化に使用される行列です。行列が提供されない場合、[ユークリッド](@ref) 平均が使用されます。
  * `tol` は収束の許容誤差です（以下を参照）。
  * `maxiter` は許可される最大反復回数です。
  * `adaptStepSize`=true（デフォルト）の場合、勾配降下のステップサイズ $ς$ は各反復で適応されます（以下を参照）。
  * `verbose`=true の場合、各反復でのステップサイズと達成された収束が印刷されます。また、収束が達成されない場合は *警告* が印刷されます。
  * ⏩=true の場合、反復はマルチスレッドで実行されます（以下を参照）。

!!! note "Nota Bene"
    [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) は、Julia が1つのスレッドのみを使用するように指示されている場合、自動的に無効になります。 [Threads](@ref) を参照してください。

    アルゴリズムが発散した場合、`verbose` が true の場合、これが発生した反復を示す **警告** が印刷されます。このアルゴリズムは一時的に発散することがありますが、収束に達することがあります。全体として、**PosDefMaifold** に実装されている他のすべての反復アルゴリズムは非常に安定していますが、これはそうではありません。

    パラメータ $p$ が小さいほど、収束は遅く、可能性が低くなります。アルゴリズムが収束しない場合は、$p$ を増やし、[`geometricMean`](@ref) の出力でアルゴリズムを初期化するか、入力セット $𝐏$ から外れ値を排除してみてください。

    `adaptStepSize` が true（デフォルト）の場合、ステップサイズ $ς$ は各反復で適応されます。そうでない場合、固定ステップサイズ $ς=1$ が使用されます。一般に、ステップサイズを適応させることで収束が早まり、収束の挙動が改善されます。

    $$
    tol
    $$

    は、データ入力 $𝐏$ の最も近い実数型の `Base.eps` の平方根にデフォルト設定されます。これは、満たす行列方程式のノルムが要素数で割られて約半分の有効数字が消失することを要求することに対応します。


**参照**: [Fisher](@ref) メトリック。

**関連**: [`geometricMean`](@ref), [`powerMean`](@ref), [`wasMean`](@ref), [`logdet0Mean`](@ref), [`mean`](@ref)。

**例**

```julia
using LinearAlgebra, PosDefManifold, Plots

# この例は、このアルゴリズムが標準の幾何平均アルゴリズムと比較して外れ値に対してより堅牢であることを示しています。

# 100個のランダムな10x10 SPD行列のセットを生成
Pset=randP(10, 100)

# 比較のために通常の幾何平均を取得
G, iter1, conv1 = geometricMean(Pset, verbose=true)

# pを変更して収束の挙動がどのように変わるかを観察
# 中央値を取得（デフォルト）
H, iter2, conv2 = geometricpMean(Pset, verbose=true)
# p=0.25 の p-平均を取得
H, iter2, conv2 = geometricpMean(Pset, 0.25, verbose=true)

println(iter1, " ", iter2); println(conv1, " ", conv2)

# Psetの最初の行列を移動して外れ値を作成する可能性があります
Pset[1]=geodesic(Fisher, G, Pset[1], 3)
G1, iter1, conv1 = geometricMean(Pset, verbose=true)
H1, iter2, conv2 = geometricpMean(Pset, 0.25, verbose=true)
println(iter1, " ", iter2); println(conv1, " ", conv2)

# 幾何平均とp-平均を、外れ値の導入前後で収集します
# ヘルミート行列のベクトル `S` に
S=HermitianVector([G, G1, H, H1])

# 幾何平均が外れ値（``G1``）の導入後にどれだけ遠くなったかを確認するために
# 幾何平均が ``H`` からどれだけ遠くなったかを確認します。すなわち、要素 (4,3) が要素 (2,1) よりもはるかに小さいことを確認します。
Δ²=distance²Mat(Float64, Fisher, S)

# これらの行列が他のすべての行列からどれだけ離れているか？
fullΔ²=Hermitian(Δ², :L)
dist=[sum(fullΔ²[:, i]) for i=1:size(fullΔ², 1)]

# スペクトル埋め込みを使用して `S` の行列をプロットします。
using Plots
Λ, U, iter, conv = laplacianEM(laplacian(Δ²), 3;  verbose=true)
plot([U[1, 1]], [U[1, 2]], seriestype=:scatter, label="g-mean")
plot!([U[2, 1]], [U[2, 2]], seriestype=:scatter, label="g-mean outlier")
plot!([U[3, 1]], [U[3, 2]], seriestype=:scatter, label="p-mean")
plot!([U[4, 1]], [U[4, 2]], seriestype=:scatter, label="p-mean outlier")

# マルチスレッドモードでアルゴリズムを実行することで得られる利点を推定します
using BenchmarkTools
Pset=randP(20, 120)
@benchmark(geometricpMean(Pset; ⏩=true)) # シングルスレッド
@benchmark(geometricpMean(Pset)) # マルチスレッド
```
