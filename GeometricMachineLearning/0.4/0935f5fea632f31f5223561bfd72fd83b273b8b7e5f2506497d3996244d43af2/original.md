```
VolumePreservingFeedForwardLayer <: AbstractExplicitLayer
```

Super-type of [`VolumePreservingLowerLayer`](@ref) and [`VolumePreservingUpperLayer`](@ref). The layers do the following: 

$$
x \mapsto \begin{cases} \sigma(Lx + b) & \text{where $L$ is }\mathtt{LowerTriangular}, \\ \sigma(Ux + b) & \text{where $U$ is }\mathtt{UpperTriangular}. \end{cases}
$$

The functor can be applied to a vector, a matrix or a tensor. The special matrices are implemented as [`LowerTriangular`](@ref) and [`UpperTriangular`](@ref).
