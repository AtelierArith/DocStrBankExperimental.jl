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

Return a [LinearFilter](@ref) object:

**(1) Maximum covariance analysis** with real or complex covariance matrix `Cxy` of dimension $n_x⋅n_y$ as input.

Differently from [PCA](@ref) and [Whitening](@ref), `Cxy` is a generic `Matrix` object since it is not symmetric/Hermitian, left alone square.

`eVar` and `eVarMeth` are keyword optional arguments for defining the [subspace dimension](@ref) $p$ using the `.arev` vector given by Eq. [mca.2].

The default values are:

  * `eVar=0.999`
  * `eVarMeth=searchsortedfirst`

If `simple` is set to `true`, $p$ is set equal to $min(n_x, n_y)$ and only the fields `.F` and `.iF` are written in the constructed object. This option is provided for low-level work when you don't need to define a subspace dimension or you want to define it by your own methods.

**(2) Maximum covariance analysis** with real or complex data matrices `X` and `Y` as input.

`dims`, `meanX`, `meanY` and `wXY` are optional keyword arguments to regulate the estimation of the cross-covariance matrix $C_{xy}$. Particularly (see [covariance matrix estimations](@ref)),

  * `meanX` is the `mean` argument for data matrix `X`.
  * `meanY` is the `mean` argument for data matrix `Y`.
  * `wXY` is the weight argument for estimating a weighted cross-covariance matrix $C_{XY}$.

Once the cross-covariance matrix estimated, method (1) is invoked with optional keyword arguments `eVar`, `eVarMeth` and `simple`. See method (1) for details.

**(3) Maximum covariance analysis** with two vectors of real or complex data matrices `𝐗` and `𝐘` as input. `𝐗` and `𝐘` must hold the same number of matrices and corresponding pairs of matrices therein must comprise the same number of samples.

`dims`, `meanX` and `meanY` are optional keyword arguments to regulate the estimation of the cross-covariance matrices for all pairs of corresponding data matrices in `𝐗` and `𝐘`. See method (2) and [covariance matrix estimations](@ref).

The arithmetic mean of these cross-covariance matrices is computed and method (1) is invoked with optional keyword arguments `eVar`, `eVarMeth` and `simple`. See method (1) for details.

**See also:** [PCA](@ref), [CCA](@ref), [gMCA](@ref), [mAJD](@ref).

**Examples:**

```julia
using Diagonalizations, LinearAlgebra, PosDefManifold, Test

# Method (1) real
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

# Method (1) complex
Xc=genDataMatrix(ComplexF64, n, t)
Yc=genDataMatrix(ComplexF64, n, t)
Cxc=Symmetric((Xc*Xc')/t)
Cyc=Symmetric((Yc*Yc')/t)
Cxyc=(Xc*Yc')/t
mCc=mca(Cxyc, simple=true)
@test Cxyc≈mCc.F[1]*mCc.D*mCc.F[2]'
Dc=mCc.F[1]'Cxyc*mCc.F[2]
@test norm(Dc-Diagonal(Dc))+1. ≈ 1.


# Method (2) real
mXY=mca(X, Y, simple=true)
D=mXY.F[1]'*Cxy*mXY.F[2]
@test norm(D-Diagonal(D))+1≈1.
@test mXY==mC

# Method (2) complex
mXYc=mca(Xc, Yc, simple=true)
Dc=mXYc.F[1]'*Cxyc*mXYc.F[2]
@test norm(Dc-Diagonal(Dc))+1. ≈ 1.
@test mXYc==mCc


# Method (3) real
# maximum covariance analysis of the average covariance and cross-covariance
k=10
Xset=[genDataMatrix(n, t) for i=1:k]
Yset=[genDataMatrix(n, t) for i=1:k]

m=mca(Xset, Yset)

# ... selecting subspace dimension allowing an explained variance = 0.5
m=mca(Xset, Yset; eVar=0.5)

# ... subtracting the mean from the matrices in Xset and Yset
m=mca(Xset, Yset; meanX=nothing, meanY=nothing, eVar=0.5)

# mca on the average of the covariance and cross-covariance matrices
# computed along dims 1
m=mca(Xset, Yset; dims=1, eVar=0.5)

# name of the filter
m.name

using Plots
# plot regularized accumulated eigenvalues
plot(m.arev)

# plot the original cross-covariance matrix and the rotated
# cross-covariance matrix
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
# Method (3) complex
# maximum covariance analysis of the average covariance and cross-covariance

k=10
Xcset=[genDataMatrix(ComplexF64, n, t) for i=1:k]
Ycset=[genDataMatrix(ComplexF64, n, t) for i=1:k]

mc=mca(Xcset, Ycset)

# ... selecting subspace dimension allowing an explained variance = 0.5
mc=mca(Xcset, Ycset; eVar=0.5)

# ... subtracting the mean from the matrices in Xset and Yset
mc=mca(Xcset, Ycset; meanX=nothing, meanY=nothing, eVar=0.5)

# mca on the average of the covariance and cross-covariance matrices
# computed along dims 1
mc=mca(Xcset, Ycset; dims=1, eVar=0.5)

# name of the filter
mc.name
```
