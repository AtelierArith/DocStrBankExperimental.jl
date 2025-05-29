```julia
(1)
function mca(Cxy :: Mat;
             eVar      :: TeVaro = ○,
             eVarMeth  :: Function = searchsortedfirst,
             simple    :: Bool = false)

(2)
function mca(X::Mat, Y::Mat;
             dims     :: Into = ○,
             meanX    :: Tmean = 0,
             meanY    :: Tmean = 0,
             wXY      :: Tw = ○,
          eVar     :: TeVaro = ○,
          eVarMeth :: Function = searchsortedfirst,
          simple   :: Bool = false)

(3)
function mca(𝐗::VecMat, 𝐘::VecMat;
             dims     :: Into = ○,
             meanX    :: Into = 0,
             meanY    :: Into = 0,
          eVar     :: TeVaro = ○,
          eVarMeth :: Function = searchsortedfirst,
          simple   :: Bool = false)
```

[LinearFilter](@ref) オブジェクトを返します：

**(1) 最大共分散分析** 実数または複素数の共分散行列 `Cxy` を入力として受け取ります。次元は $n_x⋅n_y$ です。

[PCA](@ref) や [Whitening](@ref) とは異なり、`Cxy` は対称/エルミートでなく、正方行列でもないため、一般的な `Matrix` オブジェクトです。

`eVar` と `eVarMeth` は、式 [mca.2] によって与えられる `.arev` ベクトルを使用して [部分空間次元](@ref) $p$ を定義するためのキーワードオプション引数です。

デフォルト値は次のとおりです：

  * `eVar=0.999`
  * `eVarMeth=searchsortedfirst`

`simple` が `true` に設定されている場合、$p$ は $min(n_x, n_y)$ に等しく設定され、構築されたオブジェクトには `.F` と `.iF` のフィールドのみが書き込まれます。このオプションは、部分空間次元を定義する必要がない場合や、自分の方法で定義したい場合の低レベルの作業のために提供されています。

**(2) 最大共分散分析** 実数または複素数のデータ行列 `X` と `Y` を入力として受け取ります。

`dims`、`meanX`、`meanY` および `wXY` は、クロス共分散行列 $C_{xy}$ の推定を調整するためのオプションのキーワード引数です。特に（[共分散行列の推定](@ref) を参照）、

  * `meanX` はデータ行列 `X` の `mean` 引数です。
  * `meanY` はデータ行列 `Y` の `mean` 引数です。
  * `wXY` は加重クロス共分散行列 $C_{XY}$ を推定するための重み引数です。

クロス共分散行列が推定されると、メソッド (1) がオプションのキーワード引数 `eVar`、`eVarMeth` および `simple` と共に呼び出されます。詳細はメソッド (1) を参照してください。

**(3) 最大共分散分析** 実数または複素数のデータ行列 `𝐗` と `𝐘` の2つのベクトルを入力として受け取ります。`𝐗` と `𝐘` は同じ数の行列を保持し、対応する行列のペアは同じ数のサンプルを含む必要があります。

`dims`、`meanX` および `meanY` は、`𝐗` と `𝐘` のすべての対応するデータ行列のクロス共分散行列の推定を調整するためのオプションのキーワード引数です。メソッド (2) および [共分散行列の推定](@ref) を参照してください。

これらのクロス共分散行列の算術平均が計算され、メソッド (1) がオプションのキーワード引数 `eVar`、`eVarMeth` および `simple` と共に呼び出されます。詳細はメソッド (1) を参照してください。

**関連項目：** [PCA](@ref)、[CCA](@ref)、[gMCA](@ref)、[mAJD](@ref)。

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
mC=mca(Cxy, simple=true)
@test Cxy≈mC.F[1]*mC.D*mC.F[2]'
D=mC.F[1]'Cxy*mC.F[2]
@test norm(D-Diagonal(D))+1. ≈ 1.

# メソッド (1) 複素数
Xc=genDataMatrix(ComplexF64, n, t)
Yc=genDataMatrix(ComplexF64, n, t)
Cxc=Symmetric((Xc*Xc')/t)
Cyc=Symmetric((Yc*Yc')/t)
Cxyc=(Xc*Yc')/t
mCc=mca(Cxyc, simple=true)
@test Cxyc≈mCc.F[1]*mCc.D*mCc.F[2]'
Dc=mCc.F[1]'Cxyc*mCc.F[2]
@test norm(Dc-Diagonal(Dc))+1. ≈ 1.


# メソッド (2) 実数
mXY=mca(X, Y, simple=true)
D=mXY.F[1]'*Cxy*mXY.F[2]
@test norm(D-Diagonal(D))+1≈1.
@test mXY==mC

# メソッド (2) 複素数
mXYc=mca(Xc, Yc, simple=true)
Dc=mXYc.F[1]'*Cxyc*mXYc.F[2]
@test norm(Dc-Diagonal(Dc))+1. ≈ 1.
@test mXYc==mCc


# メソッド (3) 実数
# 平均共分散とクロス共分散の最大共分散分析
k=10
Xset=[genDataMatrix(n, t) for i=1:k]
Yset=[genDataMatrix(n, t) for i=1:k]

m=mca(Xset, Yset)

# ... 説明された分散が 0.5 になるように部分空間次元を選択
m=mca(Xset, Yset; eVar=0.5)

# ... Xset と Yset の行列から平均を引く
m=mca(Xset, Yset; meanX=nothing, meanY=nothing, eVar=0.5)

# 共分散とクロス共分散行列の平均に対する mca
# 次元 1 に沿って計算された
m=mca(Xset, Yset; dims=1, eVar=0.5)

# フィルタの名前
m.name

using Plots
# 正則化された累積固有値をプロット
plot(m.arev)

# 元のクロス共分散行列と回転された
# クロス共分散行列をプロット
 Cmax=maximum(abs.(Cxy));
 h1 = heatmap(Cxy, clim=(-Cmax, Cmax), yflip=true, c=:bluesreds, title="Cxy");
 D=mC.F[1]'*Cxy*mC.F[2];
 Dmax=maximum(abs.(D));
 h2 = heatmap(D, clim=(0, Dmax), yflip=true, c=:amp, title="F[1]'*Cxy*F[2]");
 📈=plot(h1, h2, size=(700,300))
# savefig(📈, homedir()*"\Documents\Code\julia\Diagonalizations\docs\src\assets\FigMCA.png")
```

![Figure MCA](assets/FigMCA.png)

```julia
# メソッド (3) 複素数
# 平均共分散とクロス共分散の最大共分散分析

k=10
Xcset=[genDataMatrix(ComplexF64, n, t) for i=1:k]
Ycset=[genDataMatrix(ComplexF64, n, t) for i=1:k]

mc=mca(Xcset, Ycset)

# ... 説明された分散が 0.5 になるように部分空間次元を選択
mc=mca(Xcset, Ycset; eVar=0.5)

# ... Xset と Yset の行列から平均を引く
mc=mca(Xcset, Ycset; meanX=nothing, meanY=nothing, eVar=0.5)

# 共分散とクロス共分散行列の平均に対する mca
# 次元 1 に沿って計算された
mc=mca(Xcset, Ycset; dims=1, eVar=0.5)

# フィルタの名前
mc.name
```
