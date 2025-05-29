```julia
mutable struct Recenter <: Conditioner
    metric 
    eVar 
    w 
    ✓w 
    init 
    tol 
    verbose 
    forcediag 
    threaded 
    ## Fitted parameters
    Z 
    iZ 
```

Mutable structure for the **recentering** conditioner. 

Given a set of `n·n` points $𝐏$ in the manifold of positive-definite matrices, transform the set such as 

$ZP_jZ^T, \ j=1,...,k$,

where $Z$ is the whitening matrix of the barycenter of $𝐏$ as specified by the conditioner, *i.e.*, if $G$ is the barycenter of $𝐏$, then $ZGZ^T=I$.

After recentering the barycenter becomes the identity matrix and the mean of the eigenvalues of the whitened matrices is 1. In the manifold of positive-definite matrices, recentering is equivalent to parallel transport of all points to the identity barycenter, according to a given metric.

Depending on the `eVar` value used to define the [`Recenter`](@ref) conditioner, matrices $Z$ may determine a dimensionality reduction of the input points as well. In this case $Z$ is not square, but a wide matrix of dimension $p·n$, with $p<n$.

This conditoner may behave in a **supervised** way; providing the class labels  when it is fitted (see [`fit!`](@ref)), the classes are equally weighted to compute the barycenter $G$, like [`tsWeights`](@ref)`` does for computing the barycenter used for tangent space mapping. If the classes are balanced, the weighting has no effect.

This conditoner structure has the following fields:

  * `.metric`, of type  [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1), is to be specified by the user. It is the metric that will be adopted to compute the class means and the distances to the mean. default: `PosDefManifold.Euclidean`.
  * `.eVar`, the desired explained variance for the whitening. It can be a Real, Int or `nothing`. See the documentation of method [whitening](https://marco-congedo.github.io/Diagonalizations.jl/dev/whitening/#Diagonalizations.whitening) in Diagonalizations.jl. It is 0.9999 by default.
  * Fields `.w`, `.✓w`, `.init` and `.tol` are passed to the [mean](https://marco-congedo.github.io/PosDefManifold.jl/latest/riemannianGeometry/#Statistics.mean) method of PosDefManifold.jl for computing the barycenter $G$. Refer to the documentation therein for details.
  * `.verbose` is a boolean determining if information is to be printed to the REPL when using `fit!` and `transform!` with this conditioner. It is false by default.
  * `.forcediag` is a boolean for forcing diagonalization. It is true by default. If false, whitening is carried out only if a dimensionality reduction is needed, as determined by `eVar`.
  * If `.threaded` is true (default), all operations are multi-threaded.

For constructing an instance, `metric` is an argument, while `eVar`, `w`, `✓w`,  `init`, `tol`, `verbose`, `forcediag` and `threaded` are optional keyword arguments.

**Fitted parameters**

When the conditioner is fitted, the following fields are written:

  * `.Z`, the whitening matrix of the fitted set $P_j, \ j=1,...,k$, such that $ZP_jZ^T$ is whitened;
  * `.iZ`, the left inverse $Z^*$ of Z, such that $Z^*Z=I$ (identity matrix) if no dimensionality reduction is operated.

If dimensionality reduction is operated, $Z^*Z≠I$ has rank $p$.

**Examples**:

```julia
using PosDefManifoldML, PosDefManifold

# Create a default conditioner
R = Recenter(PosDefManifold.Euclidean)

# Since the Euclidean metric is the default metric,
# this is equivalent to
R = Recenter()

# Do not perform dimensionality reduction
R = Recenter(PosDefManifold.Fisher; eVar=nothing)

# Reduce the dimension to 10
R = Recenter(PosDefManifold.Fisher; eVar=10)

# Determine the dimension so as to explain at least 90% of the variance
R = Recenter(PosDefManifold.Fisher; eVar=0.9)

# Use class labels to balance the weights across classes
# (let `y` be a vector of int holding the class labels)
R = Recenter(PosDefManifold.Fisher; labels=y)

```

**See also**: [`fit!`](@ref), [`transform!`](@ref), [`crval`](@ref)
