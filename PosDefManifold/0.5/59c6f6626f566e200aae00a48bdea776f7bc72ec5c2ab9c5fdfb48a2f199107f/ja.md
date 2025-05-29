```julia
    (1) mean(metric::Metric, P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex

    (2) mean(metric::Metric, D::𝔻{T}, E::𝔻{T}) where T<:Real

    (3) mean(metric::Metric, 𝐏::ℍVector;
        <
        w::Vector=[],
        ✓w=true,
        init::Union{ℍ, Nothing}=nothing,
        tol::Real=0.,
        verbose=false,
        ⏩=true >)

    (4) mean(metric::Metric, 𝐃::𝔻Vector;
    < same optional keyword arguments as in (3) >)
```

(1) 指定された `metric` のタイプ [Metric::Enumerated type](@ref) を使用して、任意の順序で引数 $P$ と $Q$ として渡された2つの正定値行列の平均。すべての **PosDefManifold** に実装されているメトリックは対称であるため、順序は任意です。これは測地線の中点です。2つの正定値行列の加重平均を使用するには、代わりに [`geodesic`](@ref) 関数を使用してください。$P$ と $Q$ は `Hermitian` としてフラグ付けされる必要があります。行列の [型キャスティング](@ref) を参照してください。

(2) (1) と同様ですが、2つの実対角正定値行列 $D$ と $E$ の場合です。

(3) 1次元配列 $𝐏$ の [Fréchet mean](@ref) $𝐏={P_1,...,P_k}$ の $k$ 個の正定値行列、[ℍVector type](@ref) のオプションの非負実重み $w={w_1,...,w_k}$ を使用し、(1) と同様に指定された `metric` を使用します。

(4) 1次元配列 $𝐃$ の [Fréchet mean](@ref) $𝐃={D_1,...,D_k}$ の $k$ 個の正定値行列、[𝔻Vector type](@ref) のオプションの非負実重み $w={w_1,...,w_k}$ を使用し、(1) と同様に指定された `metric` を使用します。

*<optional keyword argument>* $w$ を持つ重みベクトルを渡さない場合、*無加重平均* を返します。

*<optional keyword argument>* `✓w=true` (デフォルト) の場合、重みは1に合計されるように正規化されます。そうでない場合は、渡されたまま使用され、すでに正規化されている必要があります。このオプションは、同じ重みベクトルを毎回正規化することなく、この関数を繰り返し呼び出すことを可能にするために提供されています。

(3) の `Fisher`、`logdet0` および `Wasserstein` メトリックと (4) の `logdet0` メトリックを採用すると、平均は反復アルゴリズムによって計算されます。これらのアルゴリズムの特定の初期化は、*<optional keyword argument>* `init` としてエルミート行列を渡すことで提供できます。これらのアルゴリズムの収束は、*<optional keyword argument>* `tol` によって与えられる許容誤差が必要です。`verbose=true` の場合、各反復で達成された収束が印刷されます。アルゴリズムが発散したかどうかなどの他の情報も印刷されます。これらの平均を計算するための他のオプションについては、直接関数 [`geometricMean`](@ref)、[`logdet0Mean`](@ref) および [`wasMean`](@ref) を呼び出してください。これらの関数のデフォルト値 `tol` の意味については、ドキュメントを参照してください。また、ここから呼び出すことができないロバスト平均関数 [`geometricpMean`](@ref) も参照してください。引数 `init` と `tol` は、(3) および (4) のメソッドで前述のメトリックにのみ影響します。

(3) と (4) の場合、`⏩=true` (デフォルト) の場合、すべてのメトリックの平均の計算はマルチスレッドで行われます。

!!! note "Nota Bene"
    [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) は、Julia が1つのスレッドのみを使用するように指示されている場合、自動的に無効になります。 [Threads](@ref) を参照してください。


## 数学

$$
k
$$

個の行列 ${P_1, P_2,..., P_k}$ の重み付き Fréchet mean ${w_1, w_2,..., w_k}:\sum_{i=1}^{k}w_i=1$ のサポートされているメトリックのための、閉じた形式の表現を持つものは次の通りです：

|    メトリック     | 重み付き Fréchet mean                                                         |
|:------------:|:------------------------------------------------------------------------- |
|    ユークリッド    | $\sum_{i=1}^{k}w_i P_i$                                                   |
| invEuclidean | $\big(\sum_{i=1}^{k}w_i P_i^{-1}\big)^{-1}$                               |
| ChoEuclidean | $TT^*$, ここで $T=bL_P + aL_Q$                                               |
| logEuclidean | $\textrm{exp}\big(\sum_{i=1}^{k}w_i\hspace{1pt} \textrm{log}P_i \big)$    |
| logCholesky  | $TT^*$, ここで $T=\sum_{i=1}^{k}(w_kS_k)+\sum_{i=1}^{k}(w_k\textrm{log}D_k)$ |
|    ジェフリー     | $A^{1/2}\big(A^{-1/2}HA^{-1/2}\big)^{1/2}A^{1/2}$                         |

および、反復アルゴリズムによって見つかり、方程式を検証するもの：

|  メトリック   | 重み付き Fréchet mean によって検証される方程式                                       |
|:--------:|:-------------------------------------------------------------------- |
|  フィッシャー  | $\sum_{i=1}^{k}w_i\textrm{log}\big(G^{-1/2} P_k G^{-1/2}\big)=0.$    |
| logdet0  | $\sum_{i=1}^{k}w_i\big(\frac{1}{2}P_i+\frac{1}{2}G\big)^{-1}=G^{-1}$ |
| ヴォン・ノイマン | N.A.                                                                 |
| ワッサースタイン | $G=\sum_{i=1}^{k}w_i\big( G^{1/2}  P_i G^{1/2}\big)^{1/2}$           |

**凡例:** $L_X$, $S_X$ および $D_X$ は $X$ のコレスキー下三角、厳密に下三角部分および対角部分であり、したがって $S_X+D_X=L_X$,  $L_XL_X^*=X$ です。 $A$ と $H$ はそれぞれ重み付き算術平均と重み付き調和平均です。

**参照:** [geodesic](@ref), [mean](@ref), [Fréchet mean](@ref).

**例**

```julia
using LinearAlgebra, Statistics, PosDefManifold
# 2つのランダムな3x3 SPD行列を生成
P=randP(3)
Q=randP(3)
M=mean(logdet0, P, Q) # (1)
M=mean(Euclidean, P, Q) # (1)

# 複数の行列と関連する重みをリストとして渡す
# 重みベクトルは正規化する必要はありません
R=randP(3)
mean(Fisher, ℍVector([P, Q, R]); w=[1, 2, 3])

# 4つのランダムな3x3 SPD行列のセットを生成
Pset=randP(3, 4)
weights=[1, 2, 3, 1]
# エルミート行列のベクトルを渡す (ℍVector type)
M=mean(Euclidean, Pset; w=weights) # (2) 重み付きユークリッド平均
M=mean(Wasserstein, Pset)  # (2) 無加重ワッサースタイン平均
# 反復アルゴリズムを使用する際の収束情報を表示
M=mean(Fisher, Pset; verbose=true)

# 行列の数が多い場合はマルチスレッドで実行
using BenchmarkTools
Pset=randP(20, 160)
@benchmark(mean(logEuclidean, Pset; ⏩=false)) # シングルスレッド
@benchmark(mean(logEuclidean, Pset)) # マルチスレッド
```
