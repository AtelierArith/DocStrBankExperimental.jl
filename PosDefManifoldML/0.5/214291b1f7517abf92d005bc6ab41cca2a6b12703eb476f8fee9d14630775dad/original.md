```julia
mutable struct Shrink <: Conditioner
        metric 
        radius 
        refpoint 
        reshape 
        epsilon 
        verbose 
        threaded 
        ## Fitted parameters
        γ 
        m 
        sd 
```

Mutable structure of the **geodesic shrinking** conditioner. 

Given a set of points $𝐏$ in the manifold of positive-definite matrices, this conditioner moves all points towards the identity matrix $I$ along geodesics on the manifold defined in accordance to the specified `metric`. This effectively defines a ball centered at $I$.

The step-size $γ$ of the geodesics from $I$ to each point $P$ in $𝐏$ is given by

$\gamma=\frac{r\sqrt{n}}{δ(P, I) + ϵ}$

where $r$ is the `radius` argument, $n$ is the dimension of $P$,  $δ(P, I)$ is the norm of $P$ according to the specified `metric` and $ϵ$ is an optional  small positive number given as argument `epsilon`.

The conditioner has the following fields, which are also keyword arguments that can be passed upon construction:

`.metric`, of type [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1), with default `PosDefManifold.Euclidean`.

After shrinking, the set of points $𝐏$ acquires a sought `.radius`,  which is given as optional keyword argument to the constructor (default: 0.02). This is a measure of their acquired distances from the identity (norms),  specifically, the maximum distance if `.refpoint`=:max or the mean eccentricity  if `.refpoint`=:mean (default).  In the first case the argument `radius` defines a ball confining all points, with radius equal to the maximum distance from the identity of the transformed points + $ϵ$.  In the second case, the actual radius of the ball is equal to 

$\sqrt{\frac{1}{n}\sum_{j=1}^{k}δ(P_j, I) + ϵ}$.

`.reshape`, a boolean for reshaping the eigenvalues of the set $𝐏$ after shrinking.  It applies only to the Fisher (affine-invariant) metric. Default: false. See below.

`.epsilon`, a non-negative real number, the $ϵ$ above. Default: 0.0.

`.verbose`, a boolean. If true, information is printed in the REPL. Default: false

`.threaded`, a boolean for using multi-threading. Default: true

For constructing an instance, `metric` is an argument, while `radius`, `refpoint`, `reshape`,  `epsilon`, `verbose` and `threaded` are optional keyword arguments.

**Fitted parameters**

When the conditioner is fitted, the following fields are written:

`.γ`, the step-size for geodesics (according to `metric`) from $I$ to the each matrix in $𝐏$.

`.m` and `.sd`, the mean and standard deviation of the eigenvalues of the set after shrinking. This is used for reshaping, which applies only if the Fisher metric is adopted. Reshaping is meaningful only if the input set has been recentered (see [`Recenter`](@ref)). It recenters again the eigenvalues of the set after shrinking (mean = 1),  and normalize them so as to have standard deviation equal to `.radius`.

**Examples**:

```julia
using PosDefManifoldML, PosDefManifold

# Create a conditioner adopting the Fisher Metric and use reshaping
S = Shrink(PosDefManifold.Fisher; reshape = true)
```

**See also**: [`fit!`](@ref), [`transform!`](@ref), [`crval`](@ref)
