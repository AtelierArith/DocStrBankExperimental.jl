```julia
function majd(𝑿::VecVecMat;
              covEst     :: StatsBase.CovarianceEstimator = SCM,
              dims       :: Into    = ○,
              meanX      :: Into    = 0,
          algorithm :: Symbol    = :NoJoB,
          fullModel :: Bool      = false,
          preWhite  :: Bool      = false,
          sort      :: Bool      = true,
          init      :: VecMato   = ○,
          tol       :: Real      = 0.,
          maxiter   :: Int       = _maxiter(algorithm, eltype(𝑿[1][1])),
          verbose   :: Bool      = false,
          threaded  :: Bool      = true,
        eVar     :: TeVaro   = _minDim(𝑿),
        eVarC    :: TeVaro   = ○,
        eVarMeth :: Function = searchsortedfirst,
        simple   :: Bool     = false)

```

[LinearFilter](@ref) オブジェクトを返します。

$$
k
$$

セットの $m$ データ行列 `𝐗` の **複数近似共同対角化** を、指定された解法 `algorithm` (*NoJoB* がデフォルト) を使用して行います。

`fullModel` が true の場合、上記の [gmca.3] 問題が解決されます。それ以外の場合（デフォルト）、上記の [gmca.2] 問題が解決されます。

`preWhite` が true の場合、上記のセクション [pre-whitening for MAJD](@ref) で説明されている二段階手順が使用されます。この段階で、引数 `eVarC` と `eVarMeth` を使用して次元削減を行うことができます。

デフォルト値は次のとおりです：

  * `eVarC` は 0.999 に設定されます
  * `eVarMeth=searchsortedfirst` に設定されます。

`sort` が true の場合（デフォルト）、行列 $F_1,...,F_m$ の列ベクトルは、上記の [permutation for MAJD](@ref) で説明されているように符号付けおよび順序付けされます。それ以外の場合、符号は任意であり、順序も任意になります。

`verbose` が true の場合（デフォルトは false）、各反復で達成された収束が REPL に印刷されます。

`eVar` と `eVarMeth` は、累積された正則化固有値を使用して [subspace dimension](@ref) $p$ を定義するために使用されます。式 [gmca.7] に基づいています。

デフォルト値は次のとおりです：

  * `eVar` は `𝐗` の行列の最小次元に設定されます
  * `eVarMeth=searchsortedfirst` に設定されます。

`simple` が `true` に設定されている場合、$p$ は `𝐗` の行列に対して計算された共分散行列の次元に等しく設定され、これは `dims` の選択に依存します。また、構築されたオブジェクトにはフィールド `.F` と `.iF` のみが書き込まれます。これは、近似対角化アルゴリズムの典型的な出力に対応します。

`threaded` が true（デフォルト）で、Julia に指示されたスレッド数（`Threads.nthreads()` の出力）が 1 より大きい場合、マルチスレッドをサポートする解法アルゴリズムはマルチスレッドモードで実行されます。[Algorithms](@ref) およびマルチスレッドに関する [これらのノート](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Threads-1) を参照してください。

**関連情報：** [gMCA](@ref), [gCCA](@ref), [AJD](@ref)。

**例：**

```julia
using Diagonalizations, LinearAlgebra, PosDefManifold, Test

##  k>1, m>1 の場合のテストデータを作成 ##
# `t` はサンプル数、
# `m` はデータセットの数、
# `k` は観測数、
# `n` は変数の数、
# `noise` は 1.0 より小さくなければなりません。ノイズが小さいほど、データは相関が強くなります。
# m データ行列の k ベクトルを出力します。
function getData(t, m, k, n, noise)
    # m 個の同一データ行列を作成し、異なる
    # ランダム直交行列 V_1,...,V_m によって回転させます。
    𝐕=[randU(n) for i=1:m] # ランダム直交行列
    # k にわたってユニークな分散プロファイルを持つすべての被験者に共通する変数
    X=[(abs2.(randn(n))).*randn(n, t) for s=1:k]
    # 各被験者はこの共通部分に加えてランダム部分を持ちます。
    𝐗=[[𝐕[i]*((1-noise)*X[s] + noise*randn(n, t)) for i=1:m] for s=1:k]
    return 𝐗, 𝐕
end

function getData(::Type{Complex{T}}, t, m, k, n, noise) where {T<:AbstractFloat}
    # m 個の同一データ行列を作成し、異なる
    # ランダム直交行列 V_1,...,V_m によって回転させます。
    𝐕=[randU(ComplexF64, n) for i=1:m] # ランダム直交行列
    # k にわたってユニークな分散プロファイルを持つすべての被験者に共通する変数
    X=[(abs2.(randn(n))).*randn(ComplexF64, n, t) for s=1:k]
    # 各被験者はこの共通部分に加えてランダム部分を持ちます。
    𝐗=[[𝐕[i]*((1-noise)*X[s] + noise*randn(ComplexF64, n, t)) for i=1:m] for s=1:k]
    return 𝐗, 𝐕
end


# 実データ
# 非定常データの共同盲源分離を行います。
t, m, n, k, noise = 200, 5, 4, 6, 0.1
Xset, Vset=getData(t, m, k, n, noise)
𝒞=Array{Matrix}(undef, k, m, m)
for s=1:k, i=1:m, j=1:m 𝒞[s, i, j]=(Xset[s][i]*Xset[s][j]')/t end

aX=majd(Xset; fullModel=true, algorithm=:OJoB)
# 推定されたデミキシング行列の spForm インデックスと真の
# 混合行列の積は低くなければなりません。
@test mean(spForm(aX.F[i]'*Vset[i]) for i=1:m)<0.1

# NoJoB アルゴリズムを使用して同じテストを行います。
aX=majd(Xset; fullModel=true, algorithm=:NoJoB)
@test mean(spForm(aX.F[i]'*Vset[i]) for i=1:m)<0.1

# 元のクロス共分散行列と回転された
# クロス共分散行列をプロットします。

# すべての積 𝐔[i]' * 𝒞[l, i, j] * 𝐔[j] を取得します。
function _rotate_crossCov(𝐔, 𝒞, m, k)
    𝒮=Array{Matrix}(undef, k, m, m)
    @inbounds for l=1:k, i=1:m, j=1:m 𝒮[l, i, j]=𝐔[i]'*𝒞[l, i, j]*𝐔[j] end
    return 𝒮
end

# すべての `k` クロス共分散を視覚化のために
# m*n x m*n の単一行列にまとめます。
function 𝒞2Mat(𝒞::AbstractArray, m, k)
    n=size(𝒞[1, 1, 1], 1)
    C=Matrix{Float64}(undef, m*n, m*n)
    for i=1:m, j=1:m, x=1:n, y=1:n C[i*n-n+x, j*n-n+y]=𝒞[k, i, j][x, y] end
    return C
end

using Plots

Cset=[𝒞2Mat(𝒞, m, s) for s=1:k]
 Cmax=maximum(maximum(abs.(C)) for C ∈ Cset)
 h1 = heatmap(Cset[1], clim=(-Cmax, Cmax), yflip=true, c=:bluesreds, title="all cross-cov, k=1")
 h2 = heatmap(Cset[2], clim=(-Cmax, Cmax), yflip=true, c=:bluesreds, title="all cross-cov, k=2")
 h3 = heatmap(Cset[3], clim=(-Cmax, Cmax), yflip=true, c=:bluesreds, title="all cross-cov, k=3")
 h4 = heatmap(Cset[4], clim=(-Cmax, Cmax), yflip=true, c=:bluesreds, title="all cross-cov, k=4")
 h5 = heatmap(Cset[5], clim=(-Cmax, Cmax), yflip=true, c=:bluesreds, title="all cross-cov, k=5")
 h6 = heatmap(Cset[6], clim=(-Cmax, Cmax), yflip=true, c=:bluesreds, title="all cross-cov, k=6")
 📈=plot(h1, h2, h3, h4, h5, h6, size=(1200,550))
# savefig(📈, homedir()*"\Documents\Code\julia\Diagonalizations\docs\src\assets\FigmAJD1.png")

𝒮=_rotate_crossCov(aX.F, 𝒞, m, k)
 Sset=[𝒞2Mat(𝒮, m, s) for s=1:k]
 Smax=maximum(maximum(abs.(S)) for S ∈ Sset)
 h11 = heatmap(Sset[1], clim=(-Smax, Smax), yflip=true, c=:bluesreds, title="rotated cross-cov, k=1")
 h12 = heatmap(Sset[2], clim=(-Smax, Smax), yflip=true, c=:bluesreds, title="rotated cross-cov, k=2")
 h13 = heatmap(Sset[3], clim=(-Smax, Smax), yflip=true, c=:bluesreds, title="rotated cross-cov, k=3")
 h14 = heatmap(Sset[4], clim=(-Smax, Smax), yflip=true, c=:bluesreds, title="rotated cross-cov, k=4")
 h15 = heatmap(Sset[5], clim=(-Smax, Smax), yflip=true, c=:bluesreds, title="rotated cross-cov, k=5")
 h16 = heatmap(Sset[6], clim=(-Smax, Smax), yflip=true, c=:bluesreds, title="rotated cross-cov, k=6")
 📉=plot(h11, h12, h13, h14, h15, h16, size=(1200,550))
# savefig(📉, homedir()*"\Documents\Code\julia\Diagonalizations\docs\src\assets\FigmAJD2.png")

```

![Figure mAJD1](assets/FigmAJD1.png)

![Figure mAJD2](assets/FigmAJD2.png)

上記の下部の図では、回転されたクロス共分散行列は期待される *ストリップ対角* 形式を持ちます。すなわち、各ブロック $F_i^T\frac{1}{t}(X_{li}X_{lj}^T)F_j$ は、$l∈[1,...,k]$, $i,j∈[1,...,m]$ に対しておおよそ対角です。

```julia
# 複素データ
# 非定常データの共同盲源分離を行います。
t, m, n, k, noise = 200, 5, 4, 6, 0.1
Xcset, Vcset=getData(ComplexF64, t, m, k, n, noise)
𝒞=Array{Matrix}(undef, k, m, m)
for s=1:k, i=1:m, j=1:m 𝒞[s, i, j]=(Xcset[s][i]*Xcset[s][j]')/t end

aXc=majd(Xcset; fullModel=true, algorithm=:OJoB)
# 推定されたデミキシング行列の spForm インデックスと真の
# 混合行列の積は低くなければなりません。
@test mean(spForm(aXc.F[i]'*Vcset[i]) for i=1:m)<0.1

# NoJoB アルゴリズムを使用して同じテストを行います。
aXc=majd(Xcset; fullModel=true, algorithm=:NoJoB)
@test mean(spForm(aXc.F[i]'*Vcset[i]) for i=1:m)<0.1
```
