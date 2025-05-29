```julia
(1)
function pca(C :: SorH;
             eVar     :: TeVaro = nothing,
             eVarMeth :: Function = searchsortedfirst,
             simple   :: Bool = false)

(2)
function pca(X::Mat;
             covEst   :: StatsBase.CovarianceEstimator = SCM,
             dims     :: Into = ○,
             meanX    :: Tmean = 0,
             wX       :: Tw = ○,
          eVar     :: TeVaro = ○,
          eVarMeth :: Function = searchsortedfirst,
          simple   :: Bool = false)

(3)
function pca(𝐗::VecMat;
             covEst   :: StatsBase.CovarianceEstimator = SCM,
             dims     :: Into = ○,
             meanX    :: Into = 0,
          eVar     :: TeVaro = ○,
          eVarMeth :: Function = searchsortedfirst,
          simple   :: Bool = false,
       metric   :: Metric = Euclidean,
       w        :: Vector = [],
       ✓w       :: Bool = true,
       init     :: SorHo = nothing,
       tol      :: Real = 0.,
       verbose  :: Bool = false)
```

[LinearFilter](@ref) オブジェクトを返します：

**(1) 主成分分析** 実数または複素数の共分散行列 `C` を入力として使用します。

`C` は、実数の場合は `Symmetric`、実数または複素数の場合は `Hermitian` としてフラグを立てる必要があります。詳細は [データ入力](@ref) を参照してください。

`eVar` と `evarMeth` は、式 [pca.6] によって与えられる `.arev` ベクトルを使用して [部分空間次元](@ref) $p$ を定義するためのキーワードオプション引数です。デフォルト値は次のとおりです：

  * `eVar=0.999`
  * `evarMeth=searchsortedfirst`

`simple` が `true` に設定されている場合、$p$ は $n$ に等しく設定され、構築されたオブジェクトには `.F` と `.iF` のフィールドのみが書き込まれます。このオプションは、部分空間次元を定義する必要がない場合や、自分の方法で定義したい場合の低レベルの作業のために提供されています。

**(2) 主成分分析** 実数または複素数のデータ行列 `X` を入力として使用します。

`CovEst`、`dims`、`meanX`、`wX` は、`X` の共分散行列の推定を調整するためのオプションのキーワード引数です。詳細は [共分散行列の推定](@ref) を参照してください。

共分散行列が推定されると、メソッド (1) がオプションのキーワード引数 `eVar`、`eVarMeth`、`simple` と共に呼び出されます。

**(3) 主成分分析** 実数または複素数のデータ行列のベクトル `𝐗` を入力として使用します。

`CovEst`、`dims`、`meanX` は、`𝐗` 内のすべてのデータ行列の共分散行列の推定を調整するためのオプションのキーワード引数です。詳細は [共分散行列の推定](@ref) を参照してください。

これらの共分散行列の平均は、オプションのキーワード引数 `metric`、`w`、`✓w`、`init`、`tol`、`verbose` を使用して計算されます。詳細は [平均共分散行列の推定](@ref) を参照してください。デフォルトでは、算術平均が計算されます。

平均共分散行列が推定されると、メソッド (1) がオプションのキーワード引数 `eVar`、`eVarMeth`、`simple` と共に呼び出されます。

**関連項目：** [ホワイトニング](@ref)、[CSP](@ref)、[MCA](@ref)、[AJD](@ref)。

**例：**

```julia
using Diagonalizations, LinearAlgebra, PosDefManifold, Test

# メソッド (1) 実数
n, t=10, 100
X=genDataMatrix(n, t)
C=(X*X')/t
pC=pca(Hermitian(C); simple=true)
# または、短く
pC=pca(ℍ(C); simple=true)

# メソッド (1) 複素数
Xc=genDataMatrix(ComplexF64, n, t)
Cc=(Xc*Xc')/t
pCc=pca(Hermitian(Cc); simple=true)


# メソッド (2) 実数
pX=pca(X; simple=true)
@test C≈pC.F*pC.D*pC.iF
@test C≈pC.F*pC.D*pC.F'
@test pX≈pC

# メソッド (2) 複素数
pXc=pca(Xc; simple=true)
@test Cc≈pCc.F*pCc.D*pCc.iF
@test Cc≈pCc.F*pCc.D*pCc.F'
@test pXc≈pCc


# メソッド (3) 実数
k=10
Xset=[genDataMatrix(n, t) for i=1:k]

# 平均共分散行列に対するpca
p=pca(Xset)

# ... 説明された分散が0.5になるように部分空間次元を選択
p=pca(Xset; eVar=0.5)

# ... logEuclideanメトリックを使用して共分散行列を平均化
p=pca(Xset; metric=logEuclidean, eVar=0.5)

# ... 共分散行列に重み `w` を与える
p=pca(Xset; metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# ... 平均を引く
p=pca(Xset; meanX=nothing, metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# dims 1 に沿って計算された共分散行列の平均に対するpca
p=pca(Xset; dims=1)

# 説明された分散
p.eVar

# フィルタの名前
p.name

using Plots
# 正則化された累積固有値をプロット
plot(p.arev)

# 元の共分散行列と回転された共分散行列をプロット
 Cmax=maximum(abs.(C));
 h1 = heatmap(C, clim=(-Cmax, Cmax), yflip=true, c=:bluesreds, title="C");
 D=pC.F'*C*pC.F;
 Dmax=maximum(abs.(D));
 h2 = heatmap(D, clim=(0, Dmax), yflip=true, c=:amp, title="F'*C*F");
 📈=plot(h1, h2, size=(700, 300))
# savefig(📈, homedir()*"\Documents\Code\julia\Diagonalizations\docs\src\assets\FigPCA.png")
```

![Figure PCA](assets/FigPCA.png)

```julia
# メソッド (3) 複素数
k=10
Xcset=[genDataMatrix(ComplexF64, n, t) for i=1:k]

# 平均共分散行列に対するpca
pc=pca(Xcset)

# ... 説明された分散が0.5になるように部分空間次元を選択
pc=pca(Xcset; eVar=0.5)

# ... logEuclideanメトリックを使用して共分散行列を平均化
pc=pca(Xcset; metric=logEuclidean, eVar=0.5)

# ... 共分散行列に重み `w` を与える
pc=pca(Xcset; metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# ... 平均を引く
pc=pca(Xcset; meanX=nothing, metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# dims 1 に沿って計算された共分散行列の平均に対するpca
pc=pca(Xcset; dims=1)

# 説明された分散
pc.eVar

# フィルタの名前
pc.name
```
