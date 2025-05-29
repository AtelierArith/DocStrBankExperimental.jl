```julia
(1)
function whitening(C :: SorH;
                   eVar     :: TeVaro=○,
                   eVarMeth :: Function=searchsortedfirst,
                   simple   :: Bool=false)

(2)
function whitening(X::Mat;
                   covEst   :: StatsBase.CovarianceEstimator = SCM,
                   dims     :: Into = ○,
                   meanX    :: Tmean = 0,
                   wX       :: Tw = ○,
                eVar     :: TeVaro = ○,
                eVarMeth :: Function = searchsortedfirst,
                simple   :: Bool = false)

(3)
function whitening(𝐗::VecMat;
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

**(1) ホワイトニング** 実数または複素数の共分散行列 `C` を入力として使用します。

`C` は、実数の場合は `Symmetric`、複素数の場合は `Hermitian` としてフラグ付けされる必要があります。詳細は [データ入力](@ref) を参照してください。

`eVar` と `evarMeth` は、Eq. [pca.6] によって与えられる `.arev` ベクトルを使用して [部分空間次元](@ref) $p$ を定義するためのキーワードオプション引数です。デフォルト値は次のとおりです：

  * `eVar=0.999`
  * `evarMeth=searchsortedfirst`

`simple` が `true` に設定されている場合、$p$ は $n$ に等しく設定され、構築されたオブジェクトには `.F` と `.iF` のフィールドのみが書き込まれます。このオプションは、部分空間次元を定義する必要がない場合や、自分の方法で定義したい場合の低レベルの作業のために提供されています。

**(2) ホワイトニング** 実数または複素数のデータ行列 `X` を入力として使用します。

`CovEst`、`dims`、`meanX`、`wX` は、`X` の共分散行列の推定を調整するためのオプションのキーワード引数です。詳細は [共分散行列の推定](@ref) を参照してください。

共分散行列が推定されると、メソッド (1) がオプションのキーワード引数 `eVar`、`eVarMeth`、`simple` と共に呼び出されます。

**(3) ホワイトニング** 実数または複素数のデータ行列のベクトル `𝐗` を入力として使用します。

`CovEst`、`dims`、`meanX` は、`𝐗` 内のすべてのデータ行列の共分散行列の推定を調整するためのオプションのキーワード引数です。詳細は [共分散行列の推定](@ref) を参照してください。

これらの共分散行列の平均は、オプションのキーワード引数 `metric`、`w`、`✓w`、`init`、`tol`、`verbose` を使用して計算されます。詳細は [平均共分散行列の推定](@ref) を参照してください。デフォルトでは、算術平均が計算されます。

平均共分散行列が推定されると、メソッド (1) がオプションのキーワード引数 `eVar`、`eVarMeth`、`simple` と共に呼び出されます。

**関連情報：** [PCA](@ref)、[CCA](@ref)。

**例：**

```julia
using Diagonalizations, LinearAlgebra, PosDefManifold, Test

# メソッド (1) 実数
n, t=10, 100
X=genDataMatrix(n, t)
C=(X*X')/t
wC=whitening(Hermitian(C); simple=true)
# または、短く
wC=whitening(ℍ(C); simple=true)

# メソッド (1) 複素数
Xc=genDataMatrix(ComplexF64, n, t)
Cc=(Xc*Xc')/t
wCc=whitening(Hermitian(Cc); simple=true)


# メソッド (2) 実数
wX=whitening(X; simple=true)
@test wC.F'*C*wC.F≈I
@test wX.F'*C*wX.F≈I
@test wX≈wC

# メソッド (2) 複素数
wXc=whitening(Xc; simple=true)
@test wCc.F'*Cc*wCc.F≈I
@test wXc.F'*Cc*wXc.F≈I
@test wXc≈wCc


# メソッド (3) 実数
k=10
Xset=[genDataMatrix(n, t) for i=1:k]

# 平均共分散行列でのホワイトニング
w=whitening(Xset)

# ... 説明された分散が 0.5 になるように部分空間次元を選択
w=whitening(Xset; eVar=0.5)

# ... logEuclidean メトリックを使用して共分散行列を平均化
w=whitening(Xset; metric=logEuclidean, eVar=0.5)

# ... 共分散行列に重み `w` を与える
w=whitening(Xset; metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# ... 平均を引く
w=whitening(Xset; meanX=nothing, metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# dims 1 に沿って計算された共分散行列の平均でホワイトニング
w=whitening(Xset; dims=1)

# 説明された分散
w.eVar

# フィルタの名前
w.name

using Plots
# 正則化された累積固有値をプロット
plot(w.arev)

# 元の共分散行列とホワイトニングされた共分散行列をプロット
 Cmax=maximum(abs.(C));
 h1 = heatmap(C, clim=(-Cmax, Cmax), yflip=true, c=:bluesreds, title="C");
 D=wC.F'*C*wC.F;
 h2 = heatmap(D, clim=(0, 1), yflip=true, c=:amp, title="F'*C*F");
 📈=plot(h1, h2, size=(700, 300))
# savefig(📈, homedir()*"\Documents\Code\julia\Diagonalizations\docs\src\assets\FigWhitening.png")
```

![Figure Whitening](assets/FigWhitening.png)

```julia

# メソッド (3) 複素数
k=10
Xcset=[genDataMatrix(ComplexF64, n, t) for i=1:k]

# 平均共分散行列でのホワイトニング
wc=whitening(Xcset)

# ... 説明された分散が 0.5 になるように部分空間次元を選択
wc=whitening(Xcset; eVar=0.5)

# ... logEuclidean メトリックを使用して共分散行列を平均化
wc=whitening(Xcset; metric=logEuclidean, eVar=0.5)

# ... 共分散行列に重み `w` を与える
wc=whitening(Xset; metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# ... 平均を引く
wc=whitening(Xcset; meanX=nothing, metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# dims 1 に沿って計算された共分散行列の平均でホワイトニング
wc=whitening(Xcset; dims=1)

# 説明された分散
wc.eVar

# フィルタの名前
wc.name
```
