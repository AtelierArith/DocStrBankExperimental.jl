```julia
function gmca(𝐗::VecMat;
              covEst     :: StatsBase.CovarianceEstimator = SCM,
              dims       :: Into    = ○,
              meanX      :: Into    = 0,
          algorithm :: Symbol    = :OJoB,
          fullModel :: Bool      = false,
          sort      :: Bool      = true,
          init      :: VecMato   = ○,
          tol       :: Real      = 0.,
          maxiter   :: Int       = _maxiter(algorithm, eltype(𝐗[1])),
          verbose   :: Bool      = false,
          threaded  :: Bool      = true,
        eVar     :: TeVaro   = _minDim(𝐗),
        eVarMeth :: Function = searchsortedfirst,
        simple   :: Bool     = false)

```

[LinearFilter](@ref) オブジェクトを返します。

与えられた解法 `algorithm` (*OJoB* がデフォルト) を使用して、$m$ データ行列の集合 `𝐗` の **一般化最大共分散分析** を行います。

`fullModel` が true の場合、上記の [gmca.3] 問題が解かれます。そうでない場合（デフォルト）、上記の [gmca.2] 問題が解かれます。

`sort` が true の場合（デフォルト）、行列 $F_1,...,F_m$ の列ベクトルは、[gMCA のための置換](@ref) で説明されているように符号付けされ、順序が入れ替えられます。そうでない場合、符号は任意であり、順序も任意になります。

引数 `init`、`tol`、および `maxiter` については、[アルゴリズム](@ref) を参照してください。

`verbose` が true の場合（デフォルトは false）、各反復で達成された収束が REPL に出力されます。

`eVar` と `eVarMeth` は、式 [gmca.7] の累積正則化固有値を使用して [部分空間次元](@ref) $p$ を定義するために使用されます。

デフォルト値は次のとおりです：

  * `eVar` は `𝐗` の行列の最小次元に設定されます
  * `eVarMeth=searchsortedfirst`

`simple` が true に設定されている場合、$p$ は `𝐗` の行列に対して計算された共分散行列の次元に等しく設定され、`dims` の選択に依存します。また、構築されたオブジェクトには `.F` と `.iF` のフィールドのみが書き込まれます。これは、近似対角化アルゴリズムの典型的な出力に対応します。

`threaded`=true（デフォルト）で、Julia に指示されたスレッド数（Threads.nthreads() の出力）が 1 より大きい場合、マルチスレッドをサポートする解法アルゴリズムはマルチスレッドモードで実行されます。マルチスレッドに関する詳細は、[アルゴリズム](@ref) および [これらのノート](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Threads-1) を参照してください。

**関連情報：** [MCA](@ref)、[gCCA](@ref)、[mAJD](@ref)。

**例：**

```julia
using Diagonalizations, LinearAlgebra, PosDefManifold, Test


####  k=1, m>1 のケースをテストするためのデータを作成
# `t` はサンプル数、
# `m` はデータセットの数、
# `n` は変数の数、
# `noise` は 1.0 より小さくなければなりません。ノイズが小さいほど、
#  データはより相関します。
function getData(t, m, n, noise)
    # m 個の同一のデータ行列を作成し、異なる
    # ランダム直交行列 V_1,...,V_m によって回転させます
    𝐕=[randU(n) for i=1:m] # ランダム直交行列
    X=randn(n, t)  # すべての被験者に共通のデータ
    # 各被験者はこの共通部分に加えてランダム部分を持ちます
    𝐗=[𝐕[i]'*((1-noise)*X + noise*randn(n, t)) for i=1:m]
    return 𝐗
end

function getData(::Type{Complex{T}}, t, m, n, noise) where {T<:AbstractFloat}
    # m 個の同一のデータ行列を作成し、異なる
    # ランダム直交行列 V_1,...,V_m によって回転させます
    𝐕=[randU(ComplexF64, n) for i=1:m] # ランダム直交行列
    X=randn(ComplexF64, n, t)  # すべての被験者に共通のデータ
    # 各被験者はこの共通部分に加えてランダム部分を持ちます
    𝐗=[𝐕[i]'*((1-noise)*X + noise*randn(ComplexF64, n, t)) for i=1:m]
    return 𝐗
end


# 実データ：m=2 の場合、gMCA が MCA と同じ結果を返すことを確認
t, m, n, noise = 20, 2, 6, 0.1
Xset=getData(t, m, n, noise)
Cx=(Xset[1]*Xset[1]')/t
Cy=(Xset[2]*Xset[2]')/t
Cxy=(Xset[1]*Xset[2]')/t

gm=gmca(Xset; simple=true)
m=mca(Cxy; simple=true)

@test (m.F[1]'*Cxy*m.F[2]) ≈ (gm.F[1]'*Cxy*gm.F[2])
# 次の行列は、可能な符号の曖昧さから出てくる単位行列である必要があります
@test abs.(m.F[1]'*gm.F[1]) ≈ I
@test abs.(m.F[2]'*gm.F[2]) ≈ I

# 複素データ：m=2 の場合、gMCA が MCA と同じ結果を返すことを確認
t, m, n, noise = 20, 2, 6, 0.1
Xcset=getData(ComplexF64, t, m, n, noise)
Ccx=(Xcset[1]*Xcset[1]')/t
Ccy=(Xcset[2]*Xcset[2]')/t
Ccxy=(Xcset[1]*Xcset[2]')/t

gmc=gmca(Xcset; simple=true)
mc=mca(Ccxy; simple=true)

# 複素データの場合、ベクトルの順序が任意であるため、単純なチェックを行います
@test spForm(mc.F[1]'gmc.F[1])<0.01
@test spForm(mc.F[2]'gmc.F[2])<0.01


# 実データ：m>2 の場合
t, m, n, noise = 20, 4, 6, 0.1
Xset=getData(t, m, n, noise)

# ... 説明された分散が 0.9 になるように部分空間次元を選択
gm=gmca(Xset, eVar=0.9)

# フィルタの名前
gm.name

𝒞=Array{Matrix}(undef, 1, m, m)
for i=1:m, j=1:m 𝒞[1, i, j]=(Xset[i]*Xset[j]')/t end

using Plots
# 正則化された累積固有値をプロット
plot(gm.arev)


# 元のクロス共分散行列と回転された
# クロス共分散行列をプロット

# すべての積 𝐔[i]' * 𝒞[l, i, j] * 𝐔[j] を取得
function _rotate_crossCov(𝐔, 𝒞, m, k)
    𝒮=Array{Matrix}(undef, k, m, m)
    @inbounds for l=1:k, i=1:m, j=1:m 𝒮[l, i, j]=𝐔[i]'*𝒞[l, i, j]*𝐔[j] end
    return 𝒮
end


# 可視化のために、すべてのクロス共分散を m*n x m*n の単一行列にまとめる
function 𝒞2Mat(𝒞::AbstractArray, m, k)
    n=size(𝒞[1, 1, 1], 1)
    C=Matrix{Float64}(undef, m*n, m*n)
    for i=1:m, j=1:m, x=1:n, y=1:n C[i*n-n+x, j*n-n+y]=𝒞[k, i, j][x, y] end
    return C
end

 C=𝒞2Mat(𝒞, m, 1)
 Cmax=maximum(abs.(C));
 h1 = heatmap(C, clim=(-Cmax, Cmax), yflip=true, c=:bluesreds, title="すべてのクロス共分散")
 𝒮=_rotate_crossCov(gm.F, 𝒞, m, 1)
 S=𝒞2Mat(𝒮, m, 1)
 Smax=maximum(abs.(S));
 h2 = heatmap(S, clim=(0, Smax), yflip=true, c=:amp, title="すべての回転されたクロス共分散")
 📈=plot(h1, h2, size=(700,300))
# savefig(📈, homedir()*"\Documents\Code\julia\Diagonalizations\docs\src\assets\FiggMCA.png")

```

![Figure gMCA](assets/FiggMCA.png)

上記の図では、回転されたクロス共分散行列は期待される *ストリップ対角* 形式を持ちます。すなわち、各ブロック $F_i^T\frac{1}{t}(X_iX_j^T)F_j$ は、$i,j∈[1,...,m]$ に対しておおよそ対角です。各ブロックは $5⋅5$ であり、`eVar=0.9` を設定することで部分空間次元が 5 に設定されています。

```julia
# 複素データ：m>2 の場合
t, m, n, noise = 20, 4, 6, 0.1
Xcset=getData(ComplexF64, t, m, n, noise)

# ... 説明された分散が 0.9 になるように部分空間次元を選択
gmc=gmca(Xcset, eVar=0.9)
```
