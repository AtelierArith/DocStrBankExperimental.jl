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

Return a [LinearFilter](@ref) object:

(1) **Common spatio-temporal pattern** with $n⋅m$ mean data matrix `X`, $m⋅m$ covariance matrices `C₍₁₎` and $n⋅n$ covariance matrix `C₍₂₎` as input.

`eVar`, `eVarC` and `eVarMeth` are keyword optional arguments for defining the [subspace dimension](@ref) $p$. Particularly:

  * `eVarC` is used for defining the subspace dimension of  the whitening step. The default is 0.999.
  * `eVar` is the keyword optional argument for defining the  [subspace dimension](@ref) $p$ using the `.arev` vector  given by [cstp.5]. The default is given in [cstp.6] here above.
  * `eVarMeth` applies to both `eVarC` and `eVar`. The default value is  `evarMeth=searchsortedfirst`.

If `simple` is set to `true`, $p$ is set equal to $n$ and only the fields `.F` and `.iF` are written in the constructed object. This option is provided for low-level work when you don't need to define a subspace dimension or you want to define it by your own methods.

(2) **Common spatio-temporal pattern** with a set of $k$ data matrices `𝐗` as input.

The $k$ matrices in `𝐗` are real or complex data matrices. They must all have the same size.

`covEst`, `meanXd₁` and `meanXd₂` are optional keyword arguments to regulate the estimation of the covariance matrices of the data matrices in `𝐗`, to be used to compute the mean covariance matrices in [cstp.2] here above. See [covariance matrix estimations](@ref). `meanXd₁` and `meanXd₂` are the means along dimension 1 and 2, respectively, of the data matrices in `𝐗`.

The mean covariance matrices $C_{(1)}$ and $C_{(1)}$ in [cstp.2] are computed using optional keywords arguments `metric`, `w`, `✓w`, `init1`, `init2`, `tol` and `verbose`, which allow to compute non-Euclidean means. Particularly (see [mean covariance matrix estimations](@ref)),

  * `init1` is the initialization for $C_{(1)}$,
  * `init2` is the initialization for $C_{(2)}$.

By default, the arithmetic means [cstp.2] are computed.

Once the two covariance matrices $C_{(1)}$ and $C_{(2)}$ estimated, method (1) is invoked with optional keyword arguments `eVar`, `eVarC`, `eVarMeth` and `simple`. See method (1) for details.

**Examples:**

```julia
using Diagonalizations, LinearAlgebra, PosDefManifold, Test

# Method (1) real
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

# Method (1) complex
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

# Method (2) real
c=cstp(Xset)

# ... selecting subspace dimension allowing an explained variance = 0.9
c=cstp(Xset; eVar=0.9)

# ... giving weights `w` to the covariance matrices
c=cstp(Xset; w=abs2.(randn(k)), eVar=0.9)

# ... subtracting the means
c=cstp(Xset; meanXd₁=nothing, meanXd₂=nothing, w=abs2.(randn(k)), eVar=0.9)

# explained variance
c.eVar

# name of the filter
c.name

using Plots
# plot the original covariance matrices and the transformed counterpart
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

# Method (2) complex
cc=cstp(Xcset)

# ... selecting subspace dimension allowing an explained variance = 0.9
cc=cstp(Xcset; eVar=0.9)

# ... giving weights `w` to the covariance matrices
cc=cstp(Xcset; w=abs2.(randn(k)), eVar=0.9)

# ... subtracting the mean
cc=cstp(Xcset; meanXd₁=nothing, meanXd₂=nothing,
        w=abs2.(randn(k)), eVar=0.9)

# explained variance
c.eVar

# name of the filter
c.name

```
