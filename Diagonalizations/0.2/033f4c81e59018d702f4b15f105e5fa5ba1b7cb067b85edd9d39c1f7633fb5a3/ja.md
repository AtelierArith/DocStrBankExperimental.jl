```julia
(1)
function csp(C₁ :: SorH, C₂ :: SorH;
             eVar     :: TeVaro = ○,
             eVarC    :: TeVaro = ○,
             eVarMeth :: Function = searchsortedfirst,
             selMeth  :: Symbol = :extremal,
             simple   :: Bool = false)

(2)
function csp(X₁ :: Mat, X₂ :: Mat;
             covEst   :: StatsBase.CovarianceEstimator = SCM,
             dims     :: Into = ○,
             meanX₁   :: Tmean = 0,
             meanX₂   :: Tmean = 0,
             wX₁      :: Tw = ○,
             wX₂      :: Tw = ○,
          eVar     :: TeVaro = ○,
          eVarC    :: TeVaro = ○,
          eVarMeth :: Function = searchsortedfirst,
          selMeth  :: Symbol = :extremal,
          simple   :: Bool = false)

(3)
function csp(𝐗₁::VecMat, 𝐗₂::VecMat;
             covEst   :: StatsBase.CovarianceEstimator = SCM,
             dims     :: Into = ○,
             meanX₁   :: Into = 0,
             meanX₂   :: Into = 0,
          eVar     :: TeVaro = ○,
          eVarC    :: TeVaro = ○,
          eVarMeth :: Function = searchsortedfirst,
          selMeth  :: Symbol = :extremal,
          simple   :: Bool = false,
       metric   :: Metric = Euclidean,
       w₁       :: Vector = [],
       w₂       :: Vector = [],
       ✓w       :: Bool = true,
       init₁    :: SorHo = nothing,
       init₂    :: SorHo = nothing,
       tol      :: Real = 0.,
       verbose  :: Bool = false)
```

[LinearFilter](@ref) オブジェクトを返します：

**(1) 共通空間パターン** は、次元 $n⋅n$ の共分散行列 `C_1` と `C_2` を入力として受け取ります。共分散行列の下付き文字は、それを計算するために使用される `dims` を指します（上記参照）。

`eVar`、`eVarC` および `eVarMeth` は、[部分空間次元](@ref) $p$ を定義するためのキーワードオプション引数です。特に：

  * デフォルトでは、上記で説明した二段階手順が解を見つけるために使用されます。この場合、`eVarC` はホワイトニングステップの部分空間次元を定義するために使用されます。`eVarC=0.0` が渡されると（`eVarC=0` と混同しないでください）、解は一般化固有値-固有ベクトル手順によって見つけられます。
  * `eVar` は、[部分空間次元](@ref) $p$ を [csp.5] によって与えられた `.arev` ベクトルを使用して定義するためのキーワードオプション引数です。
  * `eVarMeth` は `eVarC` と `eVar` の両方に適用されます。デフォルト値は `evarMeth=searchsortedfirst` です。

`selMeth=:extremal`（デフォルト）の場合、上記で説明した **a) 二つのクラスを分離する** ケースが考慮されます。`selMeth` に他のシンボルを指定すると、代わりに **b) 信号対雑音比を向上させる** ケースを考慮するよう指示します。

`simple` が `true` に設定されている場合、$p$ は $n$ に等しく設定され、構築されたオブジェクトには `.F` と `.iF` のフィールドのみが書き込まれます。このオプションは、部分空間次元を定義する必要がない場合や、自分の方法で定義したい場合のために提供されています。

**(2) 共通空間パターン** は、データ行列 `X₁` と `X₂` を入力として受け取ります。

`X₁` と `X₂` は実数または複素数のデータ行列です。

`covEst`、`dims`、`meanX₁`、`meanX₂`、`wX₁` および `wX₂` は、(`X₁`、`X₂`) の共分散行列 $(C_1, C_2)$ の推定を調整するためのオプションのキーワード引数です。特に（[共分散行列の推定](@ref) を参照）：

  * `meanX₁` はデータ行列 `X₁` の `mean` 引数です。
  * `meanX₂` はデータ行列 `X₂` の `mean` 引数です。
  * `wX₁` は `X₁` の加重共分散行列を推定するための `w` 引数です。
  * `wX₂` は `X₂` の加重共分散行列を推定するための `w` 引数です。
  * `covEst` は両方の共分散行列の推定に適用されます。

二つの共分散行列 $C_1$ と $C_2$ が推定されると、メソッド (1) がオプションのキーワード引数 `eVar`、`eVarC`、`eVarMeth`、`selMeth` および `simple` を使用して呼び出されます。詳細はメソッド (1) を参照してください。

**(3) 共通空間パターン** は、データ行列の二つのベクトル `𝐗₁` と `𝐗₂` を入力として受け取ります。

`𝐗₁` と `𝐗₂` は、同じ数の行列を保持する必要はなく、含まれる行列のサンプル数は任意です。

`covEst`、`dims`、`meanX₁` および `meanX₂` は、`𝐗₁` と `𝐗₂` のすべての行列の共分散行列の推定を調整するためのオプションのキーワード引数です。メソッド (2) および [共分散行列の推定](@ref) を参照してください。

平均共分散行列は、`𝐗₁` と `𝐗₂` のデータ行列から計算された共分散行列とは別に計算され、オプションのキーワード引数 `metric`、`w₁`、`w₂`、`✓w`、`init₁`、`init₂`、`tol` および `verbose` を使用します。特に（[平均共分散行列の推定](@ref) を参照）：

  * `w₁` は `𝐗₁` から計算された共分散行列の重みです。
  * `w₂` は `𝐗₂` から計算された共分散行列の重みです。
  * `init₁` は `𝐗₁` から計算された共分散行列の平均の初期化です。
  * `init₂` は `𝐗₂` から計算された共分散行列の平均の初期化です。

デフォルトでは、算術平均が計算されます。

**参照：** [CSTP](@ref)、[PCA](@ref)、[AJD](@ref)、[mAJD](@ref)。

**例：**

```julia
using Diagonalizations, LinearAlgebra, PosDefManifold, Test

# メソッド (1) 実数
t, n=50, 10
X1=genDataMatrix(n, t)
X2=genDataMatrix(n, t)
Cx1=Symmetric((X1*X1')/t)
Cx2=Symmetric((X2*X2')/t)
C=Cx1+Cx2
cC=csp(Cx1, Cx2; simple=true)
Dx1=cC.F'*Cx1*cC.F
@test norm(Dx1-Diagonal(Dx1))+1≈1.
Dx2=cC.F'*Cx2*cC.F
@test norm(Dx2-Diagonal(Dx2))+1≈1.
@test cC.F'*C*cC.F≈I
@test norm(Dx1-(I-Dx2))+1≈1.

# メソッド (1) 複素数
t, n=50, 10
X1c=genDataMatrix(ComplexF64, n, t)
X2c=genDataMatrix(ComplexF64, n, t)
Cx1c=Hermitian((X1c*X1c')/t)
Cx2c=Hermitian((X2c*X2c')/t)
Cc=Cx1c+Cx2c
cCc=csp(Cx1c, Cx2c; simple=true)
Dx1c=cCc.F'*Cx1c*cCc.F
@test norm(Dx1c-Diagonal(Dx1c))+1. ≈ 1.
Dx2c=cCc.F'*Cx2c*cCc.F
@test norm(Dx2c-Diagonal(Dx2c))+1. ≈ 1.
@test cCc.F'*Cc*cCc.F≈I
@test norm(Dx1c-(I-Dx2c))+1. ≈ 1.
@test cCc==c12c


# メソッド (2) 実数
c12=csp(X1, X2, simple=true)
Dx1=c12.F'*Cx1*c12.F
@test norm(Dx1-Diagonal(Dx1))+1≈1.
Dx2=c12.F'*Cx2*c12.F
@test norm(Dx2-Diagonal(Dx2))+1≈1.
@test c12.F'*C*c12.F≈I
@test norm(Dx1-(I-Dx2))+1≈1.
@test cC==c12

# メソッド (2) 複素数
c12c=csp(X1c, X2c, simple=true)
Dx1c=c12c.F'*Cx1c*c12c.F
@test norm(Dx1c-Diagonal(Dx1c))+1. ≈ 1.
Dx2c=c12c.F'*Cx2c*c12c.F
@test norm(Dx2c-Diagonal(Dx2c))+1. ≈ 1.
@test c12c.F'*Cc*c12c.F≈I
@test norm(Dx1c-(I-Dx2c))+1. ≈ 1.
@test cCc==c12c


# メソッド (3) 実数
# 平均共分散行列のCSP
k=10
Xset=[genDataMatrix(n, t) for i=1:k]
Yset=[genDataMatrix(n, t) for i=1:k]

c=csp(Xset, Yset)

# ... 説明された分散が0.9になるように部分空間次元を選択
c=csp(Xset, Yset; eVar=0.9)

# ... Xset と Yset の行列から平均を引く
c=csp(Xset, Yset; meanX₁=nothing, meanX₂=nothing, eVar=0.9)

# 次元 1 に沿って計算された共分散および交差共分散行列の平均でのcsp
c=csp(Xset, Yset; dims=1, eVar=0.9)

# フィルタの名前
c.name

using Plots
# 正則化された累積固有値をプロット
plot(c.arev)


# 元の共分散行列と変換された対応物をプロット
# 引数 `selMeth` が `extremal`（デフォルト）の場合の例：2クラスの分離
 cC=csp(Cx1, Cx2)
 Cx1Max=maximum(abs.(Cx1));
 h1 = heatmap(Cx1, clim=(-Cx1Max, Cx1Max), title="Cx1", yflip=true, c=:bluesreds);
 h2 = heatmap(cC.F'*Cx1*cC.F, clim=(0, 1), title="F'*Cx1*F", yflip=true, c=:amp);
 Cx2Max=maximum(abs.(Cx2));
 h3 = heatmap(Cx2, clim=(-Cx2Max, Cx2Max), title="Cx2", yflip=true, c=:bluesreds);
 h4 = heatmap(cC.F'*Cx2*cC.F, clim=(0, 1), title="F'*Cx2*F", yflip=true, c=:amp);
 CMax=maximum(abs.(C));
 h5 = heatmap(C, clim=(-CMax, CMax), title="Cx1+Cx2", yflip=true, c=:bluesreds);
 h6 = heatmap(cC.F'*C*cC.F, clim=(0, 1), title="F'*(Cx1+Cx2)*F", yflip=true, c=:amp);
 📈=plot(h1, h3, h5, h2, h4, h6, size=(800,400))
# savefig(📈, homedir()*"\Documents\Code\julia\Diagonalizations\docs\src\assets\FigCSP1.png")
```

![Figure CSP1](assets/FigCSP1.png)

```julia
# 引数 `selMeth` が `extremal` 以外の場合の例：snrを向上させる
 cC=csp(Cx1, Cx2; selMeth=:enhaceSNR)
 Cx1Max=maximum(abs.(Cx1));
 h1 = heatmap(Cx1, clim=(-Cx1Max, Cx1Max), title="Cx1", yflip=true, c=:bluesreds);
 h2 = heatmap(cC.F'*Cx1*cC.F, clim=(0, 1), title="F'*Cx1*F", yflip=true, c=:amp);
 Cx2Max=maximum(abs.(Cx2));
 h3 = heatmap(Cx2, clim=(-Cx2Max, Cx2Max), title="Cx2", yflip=true, c=:bluesreds);
 h4 = heatmap(cC.F'*Cx2*cC.F, clim=(0, 1), title="F'*Cx2*F", yflip=true, c=:amp);
 CMax=maximum(abs.(C));
 h5 = heatmap(C, clim=(-CMax, CMax), title="Cx1+Cx2", yflip=true, c=:bluesreds);
 h6 = heatmap(cC.F'*C*cC.F, clim=(0, 1), title="F'*(Cx1+Cx2)*F", yflip=true, c=:amp);
 📉=plot(h1, h3, h5, h2, h4, h6, size=(800,400))
# savefig(📉, homedir()*"\Documents\Code\julia\Diagonalizations\docs\src\assets\FigCSP2.png")

```

![Figure CSP2](assets/FigCSP2.png)

```julia
# メソッド (3) 複素数
# 平均共分散行列のCSP
k=10
Xsetc=[genDataMatrix(ComplexF64, n, t) for i=1:k]
Ysetc=[genDataMatrix(ComplexF64, n, t) for i=1:k]

cc=csp(Xsetc, Ysetc)

# ... 説明された分散が0.9になるように部分空間次元を選択
cc=csp(Xsetc, Ysetc; eVar=0.9)

# ... Xset と Yset の行列から平均を引く
cc=csp(Xsetc, Ysetc; meanX₁=nothing, meanX₂=nothing, eVar=0.9)

# 次元 1 に沿って計算された共分散および交差共分散行列の平均でのcsp
cc=csp(Xsetc, Ysetc; dims=1, eVar=0.9)

# フィルタの名前
cc.name
```
