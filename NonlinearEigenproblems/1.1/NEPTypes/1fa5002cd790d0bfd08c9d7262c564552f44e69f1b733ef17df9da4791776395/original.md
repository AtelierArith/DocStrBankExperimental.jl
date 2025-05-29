```
abstract type Proj_NEP <: NEP
```

`Proj_NEP` represents a projected `NEP`. The projection is defined as the NEP

$$
N(λ)=W^HM(λ)V
$$

where $M(λ)$ is a base NEP and `W` and `V` rectangular matrices representing a basis of the projection spaces. Instances are created with `create_proj_NEP`. See [`create_proj_NEP`](@ref) for examples.

Any `Proj_NEP` needs to implement two functions to manipulate the projection:

  * [`set_projectmatrices!`](@ref): Set matrices `W` and `V`
  * [`expand_projectmatrices!`](@ref): Effectively expand the matrices `W` and `V` with one column.
