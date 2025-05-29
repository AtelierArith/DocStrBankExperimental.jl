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

Return a [LinearFilter](@ref) object:

**(1) Principal component analysis** with real or complex covariance matrix `C` as input.

`C` must be flagged as `Symmetric`, if real, or `Hermitian`, if either real or complex, see [data input](@ref).

`eVar` and `evarMeth` are keyword optional arguments for defining the [subspace dimension](@ref) $p$ using the `.arev` vector given by Eq. [pca.6]. The default values are:

  * `eVar=0.999`
  * `evarMeth=searchsortedfirst`

If `simple` is set to `true`, $p$ is set equal to $n$ and only the fields `.F` and `.iF` are written in the constructed object. This option is provided for low-level work when you don't need to define a subspace dimension or you want to define it by your own methods.

**(2) Principal component analysis** with a real or complex data matrix `X` as input.

`CovEst`, `dims`, `meanX`, `wX` are optional keyword arguments to regulate the estimation of the covariance matrix of `X`. See [covariance matrix estimations](@ref).

Once the covariance matrix estimated, method (1) is invoked with optional keyword arguments `eVar`, `eVarMeth` and `simple`.

**(3) Principal component analysis** with a vector of real or complex data matrices `𝐗` as input.

`CovEst`, `dims` and `meanX` are optional keyword arguments to regulate the estimation of the covariance matrices for all data matrices in `𝐗`. See [covariance matrix estimations](@ref).

A mean of these covariance matrices is computed using optional keywords arguments `metric`, `w`, `✓w`, `init`, `tol` and `verbose`. See [mean covariance matrix estimations](@ref). By default, the arithmetic mean is computed.

Once the mean covariance matrix estimated, method (1) is invoked with optional keyword arguments `eVar`, `eVarMeth` and `simple`.

**See also:** [Whitening](@ref), [CSP](@ref), [MCA](@ref), [AJD](@ref).

**Examples:**

```julia
using Diagonalizations, LinearAlgebra, PosDefManifold, Test

# Method (1) real
n, t=10, 100
X=genDataMatrix(n, t)
C=(X*X')/t
pC=pca(Hermitian(C); simple=true)
# or, shortly
pC=pca(ℍ(C); simple=true)

# Method (1) complex
Xc=genDataMatrix(ComplexF64, n, t)
Cc=(Xc*Xc')/t
pCc=pca(Hermitian(Cc); simple=true)


# Method (2) real
pX=pca(X; simple=true)
@test C≈pC.F*pC.D*pC.iF
@test C≈pC.F*pC.D*pC.F'
@test pX≈pC

# Method (2) complex
pXc=pca(Xc; simple=true)
@test Cc≈pCc.F*pCc.D*pCc.iF
@test Cc≈pCc.F*pCc.D*pCc.F'
@test pXc≈pCc


# Method (3) real
k=10
Xset=[genDataMatrix(n, t) for i=1:k]

# pca on the average covariance matrix
p=pca(Xset)

# ... selecting subspace dimension allowing an explained variance = 0.5
p=pca(Xset; eVar=0.5)

# ... averaging the covariance matrices using the logEuclidean metric
p=pca(Xset; metric=logEuclidean, eVar=0.5)

# ... giving weights `w` to the covariance matrices
p=pca(Xset; metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# ... subtracting the mean
p=pca(Xset; meanX=nothing, metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# pca on the average of the covariance matrices computed along dims 1
p=pca(Xset; dims=1)

# explained variance
p.eVar

# name of the filter
p.name

using Plots
# plot regularized accumulated eigenvalues
plot(p.arev)

# plot the original covariance matrix and the rotated covariance matrix
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
# Method (3) complex
k=10
Xcset=[genDataMatrix(ComplexF64, n, t) for i=1:k]

# pca on the average covariance matrix
pc=pca(Xcset)

# ... selecting subspace dimension allowing an explained variance = 0.5
pc=pca(Xcset; eVar=0.5)

# ... averaging the covariance matrices using the logEuclidean metric
pc=pca(Xcset; metric=logEuclidean, eVar=0.5)

# ... giving weights `w` to the covariance matrices
pc=pca(Xcset; metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# ... subtracting the mean
pc=pca(Xcset; meanX=nothing, metric=logEuclidean, w=abs2.(randn(k)), eVar=0.5)

# pca on the average of the covariance matrices computed along dims 1
pc=pca(Xcset; dims=1)

# explained variance
pc.eVar

# name of the filter
pc.name
```
