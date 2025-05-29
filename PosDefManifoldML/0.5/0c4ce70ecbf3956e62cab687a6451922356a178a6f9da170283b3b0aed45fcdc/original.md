```julia
mutable struct Equalize <: Conditioner
    threaded
    β 
end
```

Mutable structure for the **equalizing** conditioner.

Given a set of points $𝐏$ in the manifold of positive-definite matrices, transform the set such as 

$β_jP_j, \ j=1,...,k$,

where the elements $β_j$ are chosen so as to minimize the Euclidean norm  of the transformed matrices individually.

Since the Euclidean norm is the Euclidean distance to the identity, equalizing  a recentered set of points minimizes the average dispersion of the set around  the identity, thus it should be performed after conditioner [`Recenter`](@ref). 

As compared to compression, equalization is more effective for reducing the distance  to the identity, however it is not an isometry.

Also, in contrast to compression, the transformation of the  matrices in set $𝐏$ is individual, so fitting equalization does not imply  a learning process - see [`fit!`](@ref).

The structure has one field only:

  * `.threaded`, determining whether the computations are multi-threaded (true by default).

For constructing an instance, only the `threaded` optional keyword argument can be used.

**Fitted parameters**

When the conditioner is fitted, the following field is written:

  * `.β`, a vector of positive scalars minimizing the Euclidean norm individually for each matrix in the fitted set.

**Examples**:

```julia
using PosDefManifoldML, PosDefManifold

# Create the conditioner
E = Equalize()
```

**See also**: [`fit!`](@ref), [`transform!`](@ref), [`crval`](@ref)
