```julia
mutable struct Tikhonov <: Conditioner
    α
    threaded 
```

Mutable structure for the **Tikhonov regularization** conditioner. 

Given a set of points $𝐏$ in the manifold of positive-definite matrices, transform the set such as 

$P_j+αI, \ j=1,...,k$,

where $I$ is the identity matrix and $α$ is a non-negative number.

This conditoner structure has two fields: 

  * `.α`, which is written in the structure when it is fitted to some data.
  * `.threaded`, to determine if the transformation is done in multi-threading mode (true by default).

For constructing an instance, `α` is an argument, while `threaded` is a optional keyword argument. 

!!! warning "This is not a data-driven conditioner"
    The `α` parameter must be given explicitly upon construction (it is zero by default).


**Examples**:

```julia
using PosDefManifoldML, PosDefManifold

# Create a conditioner
T = Tikhonov(0.001)
T = Tikhonov(0.001; threaded=false)
```

**See also**: [`fit!`](@ref), [`transform!`](@ref), [`crval`](@ref)
