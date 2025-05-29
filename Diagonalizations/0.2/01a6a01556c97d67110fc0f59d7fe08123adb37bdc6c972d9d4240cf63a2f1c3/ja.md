```julia
(1)
function cstp( X :: Mat, C₍₁₎ :: SorH, C₍₂₎ :: SorH;
               eVar     :: TeVaro = ○,
               eVarC    :: TeVaro = ○,
               eVarMeth :: Function = searchsortedfirst,
               simple   :: Bool = false)

(2)
function cstp( 𝐗::VecMat;
               covEst   :: StatsBase.CovarianceEstimator = SCM,
               meanXd₁  :: Into = 0,
               meanXd₂  :: Into = 0,
            eVar     :: TeVaro = ○,
            eVarC    :: TeVaro = ○,
            eVarMeth :: Function = searchsortedfirst,
            simple   :: Bool = false,
         metric   :: Metric = Euclidean,
         w        :: Vector = [],
         ✓w       :: Bool = true,
         init1    :: SorHo = nothing,
         init2    :: SorHo = nothing,
         tol      :: Real = 0.,
         verbose  :: Bool = false)
```

次の [LinearFilter](@ref) オブジェクトを返します：

(1) **共通の空間-時間パターン** で、$n⋅m$ の平均データ行列 `X`、$m⋅m$ の共分散行列 `C₍₁₎` および $n⋅n$ の共分散行列 `C₍₂₎` を入力とします。

`eVar`、`eVarC` および `eVarMeth` は、[部分空間次元](@ref) $p$ を定義するためのキーワードオプション引数です。特に：

  * `eVarC` は、ホワイトニングステップの部分空間次元を定義するために使用されます。デフォルトは 0.999 です。
  * `eVar` は、[cstp.5] で与えられた `.arev` ベクトルを使用して、[部分空間次元](@ref) $p$ を定義するためのキーワードオプション引数です。デフォルトは上記の [cstp.6] で与えられています。
  * `eVarMeth` は、`eVarC` と `eVar` の両方に適用されます。デフォルト値は `evarMeth=searchsortedfirst` です。

`simple` が `true` に設定されている場合、$p$ は $n$ に等しく設定され、構築されたオブジェクトには `.F` と `.iF` のフィールドのみが書き込まれます。このオプションは、部分空間次元を定義する必要がない場合や、自分の方法で定義したい場合のために提供されています。

(2) **共通の空間-時間パターン** で、$k$ のデータ行列のセット `𝐗` を入力とします。

`𝐗` の $k$ 行列は、実数または複素数のデータ行列です。すべて同じサイズでなければなりません。

`covEst`、`meanXd₁` および `meanXd₂` は、[cstp.2] で使用されるデータ行列の共分散行列の推定を調整するためのオプションのキーワード引数です。`meanXd₁` と `meanXd₂` は、それぞれ `𝐗` のデータ行列の次元 1 および 2 に沿った平均です。

[ cstp.2] の平均共分散行列 $C_{(1)}$ と $C_{(2)}$ は、オプションのキーワード引数 `metric`、`w`、`✓w`、`init1`、`init2`、`tol` および `verbose` を使用して計算され、非ユークリッド平均を計算することができます。特に（[平均共分散行列の推定](@ref)を参照）：

  * `init1` は $C_{(1)}$ の初期化です。
  * `init2` は $C_{(2)}$ の初期化です。

デフォルトでは、算術平均 [cstp.2] が計算されます。

2つの共分散行列 $C_{(1)}$ と $C_{(2)}$ が推定されると、メソッド (1) がオプションのキーワード引数 `eVar`、`eVarC`、`eVarMeth` および `simple` で呼び出されます。詳細はメソッド (1) を参照してください。

**例：**

```julia
using Diagonalizations, LinearAlgebra, PosDefManifold, Test

# メソッド (1) 実数
t, n, k=10, 20, 10
Xset = [genDataMatrix(t, n) for i = 1:k]
Xfixed=randn(t, n)./1
for i=1:length(Xset) Xset[i]+=Xfixed end
C1=Hermitian( mean((X'*X)/t for X∈Xset) )
C2=Hermitian( mean((X*X')/n for X∈Xset) )
Xbar=mean(Xset)
c=cstp(Xbar, C1, C2; simple=true)
@test c.F[1]'*C2*c.F[1]≈I
@test c.F[2]'*C1*c.F[2]≈I
Z=c.F[1]'*Xbar*c.F[2]
n=minimum(size(Z))
@test norm(Z[1:n, 1:n]-Diagonal(Z[1:n, 1:n]))+1. ≈ 1.
cX=cstp(Xset; simple=true)
@test c==cX

# メソッド (1) 複素数
t, n, k=10, 20, 10
Xcset = [genDataMatrix(ComplexF64, t, n) for i = 1:k]
Xcfixed=randn(ComplexF64, t, n)./1
for i=1:length(Xcset) Xcset[i]+=Xcfixed end
C1c=Hermitian( mean((Xc'*Xc)/t for Xc∈Xcset) )
C2c=Hermitian( mean((Xc*Xc')/n for Xc∈Xcset) )
Xcbar=mean(Xcset)
cc=cstp(Xcbar, C1c, C2c; simple=true)
@test cc.F[1]'*C2c*cc.F[1]≈I
@test cc.F[2]'*C1c*cc.F[2]≈I
Zc=cc.F[1]'*Xcbar*cc.F[2]
n=minimum(size(Zc))
@test norm(Zc[1:n, 1:n]-Diagonal(Zc[1:n, 1:n]))+1. ≈ 1.
cXc=cstp(Xcset; simple=true)
@test cc==cXc

# メソッド (2) 実数
c=cstp(Xset)

# ... 説明された分散が 0.9 になるように部分空間次元を選択
c=cstp(Xset; eVar=0.9)

# ... 共分散行列に重み `w` を与える
c=cstp(Xset; w=abs2.(randn(k)), eVar=0.9)

# ... 平均を引く
c=cstp(Xset; meanXd₁=nothing, meanXd₂=nothing, w=abs2.(randn(k)), eVar=0.9)

# 説明された分散
c.eVar

# フィルタの名前
c.name

using Plots
# 元の共分散行列と変換された対応物をプロット
c=cstp(Xset)

C1Max=maximum(abs.(C1));
 h1 = heatmap(C1, clim=(-C1Max, C1Max), title="C1", yflip=true, c=:bluesreds);
 D1=c.F[1]'*C2*c.F[1];
 D1Max=maximum(abs.(D1));
 h2 = heatmap(D1, clim=(0, D1Max), title="F[1]'*C2*F[1]", yflip=true, c=:amp);
 C2Max=maximum(abs.(C2));
 h3 = heatmap(C2, clim=(-C2Max, C2Max), title="C2", yflip=true, c=:bluesreds);
 D2=c.F[2]'*C1*c.F[2];
 D2Max=maximum(abs.(D2));
 h4 = heatmap(D2, clim=(0, D2Max), title="F[2]'*C1*F[2]", yflip=true, c=:amp);

XbarMax=maximum(abs.(Xbar));
 h5 = heatmap(Xbar, clim=(-XbarMax, XbarMax), title="Xbar", yflip=true, c=:bluesreds);
 DX=c.F[1]'*Xbar*c.F[2];
 DXMax=maximum(abs.(DX));
 h6 = heatmap(DX, clim=(0, DXMax), title="F[1]'*Xbar*F[2]", yflip=true, c=:amp);
 📈=plot(h1, h3, h5, h2, h4, h6, size=(800,400))
# savefig(📈, homedir()*"\Documents\Code\julia\Diagonalizations\docs\src\assets\FigCSTP.png")

```

![Figure CSTP](assets/FigCSTP.png)

```julia

# メソッド (2) 複素数
cc=cstp(Xcset)

# ... 説明された分散が 0.9 になるように部分空間次元を選択
cc=cstp(Xcset; eVar=0.9)

# ... 共分散行列に重み `w` を与える
cc=cstp(Xcset; w=abs2.(randn(k)), eVar=0.9)

# ... 平均を引く
cc=cstp(Xcset; meanXd₁=nothing, meanXd₂=nothing,
        w=abs2.(randn(k)), eVar=0.9)

# 説明された分散
c.eVar

# フィルタの名前
c.name

```
