```julia
mutable struct Compress <: Conditioner
    threaded
    β 
end
```

Mutable structure for the **compressing** conditioner.

Given a set of points $𝐏$ in the manifold of positive-definite matrices, transform the set such as 

$βP_j, \ j=1,...,k$,

where $β$ is chosen to minimize the average Euclidean norm of the transformed set, *i.e.*, the average distance to the identity matrix according to the specifies metric.

Since the Euclidean norm is the Euclidean distance to the identity, compressing  a recentered set of points minimizes the average dispersion of the set around  the identity, thus it should be performed after conditioner [`Recenter`](@ref). 

The structure has one field only:

  * `.threaded`, determining whether the computations are multi-threaded (true by default).

For constructing an instance, only the `threaded` optional keyword argument can be used.

**Fitted parameters**

When the conditioner is fitted, the following field is written:

  * `.β`, a positive scalar minimizing the average Euclidean norm of the fitted set.

**Examples**:

```julia
using PosDefManifoldML, PosDefManifold

# Create the conditioner
C = Compress()
```

**See also**: [`fit!`](@ref), [`transform!`](@ref), [`crval`](@ref)
