```julia
(1)
function cca(Cx :: SorH, Cy :: SorH, Cxy :: Mat;
             eVarCx   :: TeVaro=○,
             eVarCy   :: TeVaro=○,
             eVar     :: TeVaro=○,
             eVarMeth :: Function=searchsortedfirst,
             simple   :: Bool=false)

(2)
function cca(X::Mat, Y::Mat;
             covEst   :: StatsBase.CovarianceEstimator=SCM,
             dims     :: Into = ○,
             meanX    :: Tmean = 0,
             meanY    :: Tmean = 0,
             wX       :: Tw = ○,
             wY       :: Tw = ○,
             wXY      :: Tw = ○,
          eVarCx   :: TeVaro = ○,
          eVarCy   :: TeVaro = ○,
          eVar     :: TeVaro = ○,
          eVarMeth :: Function = searchsortedfirst,
          simple   :: Bool = false)

(3)
function cca(𝐗::VecMat, 𝐘::VecMat;
             covEst   :: StatsBase.CovarianceEstimator=SCM,
             dims     :: Into = ○,
             meanX    :: Into = 0,
             meanY    :: Into = 0,
          eVarCx   :: TeVaro = ○,
          eVarCy   :: TeVaro = ○,
          eVar     :: TeVaro = ○,
          eVarMeth :: Function = searchsortedfirst,
          simple   :: Bool = false,
       metric   :: Metric = Euclidean,
       wCx      :: Vector = [],
       wCy      :: Vector = [],
       ✓w       :: Bool = true,
       initCx   :: SorHo = nothing,
       initCy   :: SorHo = nothing,
       tol      :: Real = 0.,
       verbose  :: Bool = false)
```

[LinearFilter](@ref) オブジェクトを返します：

**(1) 正準相関分析** では、実数または複素数の入力として：

  * 次元 $n_x⋅n_x$ の共分散行列 `Cx`、
  * 次元 $n_y⋅n_y$ の共分散行列 `Cy` および
  * 次元 $n_x⋅n_y$ の相互共分散行列 `Cxy`。

`Cx` と `Cy` は、実数の場合は `Symmetric`、複素数の場合は `Hermitian` としてフラグ付けされる必要があります。代わりに `Cxy` は一般的な `Matrix` オブジェクトであり、対称/Hermitian ではなく、正方行列でもありません。

`eVarCx`、`eVarCy`、`eVar` および `eVarMeth` は、[部分空間次元](@ref) $p$ を定義するためのキーワードオプション引数です。特に：

  * `eVarCx` と `eVarCy` は、`Cx` と `Cy` のホワイトニングにおける部分空間次元を決定するために使用されます。すなわち、上記の **解法** セクションで説明した二段階手順の最初のステップです。
  * `eVar` は、上記の Eq. [cca.5] によって与えられる `.arev` ベクトルを使用して最終的な部分空間次元を決定するために使用されます。
  * `eVarMeth` は `eVarCx`、`eVarCy` および `eVar` に適用されます。

デフォルト値は次のとおりです：

  * `eVarCx=0.999`
  * `eVarCy=0.999`
  * `eVar=0.999`
  * `eVarMeth=searchsortedfirst`

`simple` が `true` に設定されている場合、$p$ は $min(n_x, n_y)$ に設定され、構築されたオブジェクトのフィールド `.F` と `.iF` のみが書き込まれます。このオプションは、部分空間次元を定義する必要がない場合や、自分の方法で定義したい場合のために提供されています。

**(2) 正準相関分析** では、実数または複素数のデータ行列 `X` と `Y` を入力として使用します。

`covEst`、`dims`、`meanX`、`meanY`、`wX`、`wY` および `wXY` は、`X` と `Y` の共分散行列およびそれらの相互共分散行列 $C_{xy}$ の推定を調整するためのオプションのキーワード引数です。特に（[共分散行列の推定](@ref)を参照）：

  * `meanX` はデータ行列 `X` の `mean` 引数です。
  * `meanY` はデータ行列 `Y` の `mean` 引数です。
  * `wX` は加重共分散行列 $C_x$ を推定するための `w` 引数です。
  * `wY` は加重共分散行列 $C_y$ を推定するための `w` 引数です。
  * `wXY` は加重相互共分散行列 $C_{XY}$ を推定するための `w` 引数です。
  * `covEst` は $C_x$ と $C_y$ の推定にのみ適用されます。

$$
C_x
$$

、$C_y$ および $C_{xy}$ が推定されると、メソッド (1) がオプションのキーワード引数 `eVar`、`eVarCx`、`eVarCy`、`eVarMeth` および `simple` と共に呼び出されます。詳細はメソッド (1) を参照してください。

**(3) 正準相関分析** では、実数または複素数のデータ行列 `𝐗` と `𝐘` の二つのベクトルを入力として使用します。`𝐗` と `𝐘` は同じ数の行列を保持し、それに対応する行列のペアは同じ数のサンプルを含む必要があります。

`covEst`、`dims`、`meanX` および `meanY` は、すべての行列の共分散行列と、それらの対応するデータ行列のすべてのペアの相互共分散行列の推定を調整するためのオプションのキーワード引数です。メソッド (2) および [共分散行列の推定](@ref)を参照してください。

これらの共分散行列の平均が計算されます。相互共分散行列には算術平均が使用されます。`𝐗` と `𝐘` の共分散行列には、オプションのキーワード引数 `metric`、`wCx`、`wCy`、`✓w`、`initCx`、`initCy`、`tol` および `verbose` が使用され、非ユークリッド平均の推定を可能にします。特に（[平均共分散行列の推定](@ref)を参照）：

  * `wCx` は `𝐗` の共分散行列の重みです。
  * `wCy` は `𝐘` の共分散行列の重みです。
  * `initCx` は `𝐗` の共分散行列の平均の初期化です。
  * `initCy` は `𝐘` の共分散行列の平均の初期化です。

デフォルトでは、算術平均が計算されます。

平均共分散行列と相互共分散行列が推定されると、メソッド (1) がオプションのキーワード引数 `eVarCx`、`eVarCy`、`eVar`、`eVarMeth` および `simple` と共に呼び出されます。詳細はメソッド (1) を参照してください。

**参照：** [ホワイトニング](@ref)、[MCA](@ref)、[gCCA](@ref)、[mAJD](@ref)。

**例：**

```julia
using Diagonalizations, LinearAlgebra, PosDefManifold, Test

# メソッド (1) 実数
n, t=10, 100
X=genDataMatrix(n, t)
Y=genDataMatrix(n, t)
Cx=Symmetric((X*X')/t)
Cy=Symmetric((Y*Y')/t)
Cxy=(X*Y')/t
cC=cca(Cx, Cy, Cxy, simple=true)
@test cC.F[1]'*Cx*cC.F[1]≈I
@test cC.F[2]'*Cy*cC.F[2]≈I
D=cC.F[1]'*Cxy*cC.F[2]
@test norm(D-Diagonal(D))+1. ≈ 1.

# メソッド (1) 複素数
Xc=genDataMatrix(ComplexF64, n, t)
Yc=genDataMatrix(ComplexF64, n, t)
Cxc=Hermitian((Xc*Xc')/t)
Cyc=Hermitian((Yc*Yc')/t)
Cxyc=(Xc*Yc')/t
cCc=cca(Cxc, Cyc, Cxyc, simple=true)
@test cCc.F[1]'*Cxc*cCc.F[1]≈I
@test cCc.F[2]'*Cyc*cCc.F[2]≈I
Dc=cCc.F[1]'*Cxyc*cCc.F[2]
@test norm(Dc-Diagonal(Dc))+1. ≈ 1.


# メソッド (2) 実数
cXY=cca(X, Y, simple=true)
@test cXY.F[1]'*Cx*cXY.F[1]≈I
@test cXY.F[2]'*Cy*cXY.F[2]≈I
D=cXY.F[1]'*Cxy*cXY.F[2]
@test norm(D-Diagonal(D))+1. ≈ 1.
@test cXY==cC

# メソッド (2) 複素数
cXYc=cca(Xc, Yc, simple=true)
@test cXYc.F[1]'*Cxc*cXYc.F[1]≈I
@test cXYc.F[2]'*Cyc*cXYc.F[2]≈I
Dc=cXYc.F[1]'*Cxyc*cXYc.F[2]
@test norm(Dc-Diagonal(Dc))+1. ≈ 1.
@test cXYc==cCc


# メソッド (3) 実数
# 平均共分散および相互共分散の正準相関分析
k=10
Xset=[genDataMatrix(n, t) for i=1:k]
Yset=[genDataMatrix(n, t) for i=1:k]

c=cca(Xset, Yset)

# ... 説明された分散 = 0.9 を許可する部分空間次元を選択
c=cca(Xset, Yset; eVar=0.9)

# ... Xset と Yset の行列から平均を引く
c=cca(Xset, Yset; meanX=nothing, meanY=nothing, eVar=0.9)

# 共分散および相互共分散行列の平均に対する cca
# 次元 1 に沿って計算
c=cca(Xset, Yset; dims=1, eVar=0.9)

# フィルタの名前
c.name

using Plots
# 正則化された累積固有値をプロット
plot(c.arev)

# 元の共分散および相互共分散行列をプロット
# それらの変換された対応物
 CxyMax=maximum(abs.(Cxy));
 h1 = heatmap(Cxy, clim=(-CxyMax, CxyMax), title="Cxy", yflip=true, c=:bluesreds);
 D=cC.F[1]'*Cxy*cC.F[2];
 Dmax=maximum(abs.(D));
 h2 = heatmap(D, clim=(0, Dmax), title="F1'CxyF2", yflip=true, c=:amp);
 CxMax=maximum(abs.(Cx));
 h3 = heatmap(Cx, clim=(-CxMax, CxMax), title="Cx", yflip=true, c=:bluesreds);
 h4 = heatmap(cC.F[1]'*Cx*cC.F[1], clim=(0, 1), title="F1'CxF1", yflip=true, c=:amp);
 CyMax=maximum(abs.(Cy));
 h5 = heatmap(Cy, clim=(-CyMax, CyMax), title="Cy", yflip=true, c=:bluesreds);
 h6 = heatmap(cC.F[2]'*Cy*cC.F[2], clim=(0, 1), title="F2'CyF2", yflip=true, c=:amp);
 📈=plot(h3, h5, h1, h4, h6, h2, size=(800,400))
# savefig(📈, homedir()*"\Documents\Code\julia\Diagonalizations\docs\src\assets\FigCCA.png")

```

![Figure CCA](assets/FigCCA.png)

```julia
# メソッド (3) 複素数
# 平均共分散および相互共分散の正準相関分析
k=10
Xcset=[genDataMatrix(ComplexF64, n, t) for i=1:k]
Ycset=[genDataMatrix(ComplexF64, n, t) for i=1:k]

cc=cca(Xcset, Ycset)

# ... 説明された分散 = 0.9 を許可する部分空間次元を選択
cc=cca(Xcset, Ycset; eVar=0.9)

# ... Xset と Yset の行列から平均を引く
cc=cca(Xcset, Ycset; meanX=nothing, meanY=nothing, eVar=0.9)

# 共分散および相互共分散行列の平均に対する cca
# 次元 1 に沿って計算
cc=cca(Xcset, Ycset; dims=1, eVar=0.9)

# フィルタの名前
cc.name
```
