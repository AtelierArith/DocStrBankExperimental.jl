```
Dirichlet(u::Symbol, ∂Ω::AbstractVecOrSet, f::Function, components=nothing)
```

Create a Dirichlet boundary condition on `u` on the `∂Ω` part of the boundary. `f` is a function of the form `f(x)` or `f(x, t)` where `x` is the spatial coordinate and `t` is the current time, and returns the prescribed value. `components` specify the components of `u` that are prescribed by this condition. By default all components of `u` are prescribed.

The set, `∂Ω`, can be an `AbstractSet` or `AbstractVector` with elements of type [`FacetIndex`](@ref), [`FaceIndex`](@ref), [`EdgeIndex`](@ref), [`VertexIndex`](@ref), or `Int`. For most cases, the element type is `FacetIndex`, as shown below. To constrain a single point, using `VertexIndex` is recommended, but it is also possible to constrain a specific nodes by giving the node numbers via `Int` elements. To constrain e.g. an edge in 3d `EdgeIndex` elements can be given.

For example, here we create a Dirichlet condition for the `:u` field, on the facetset called `∂Ω` and the value given by the `sin` function:

*Examples*

```jldoctest
# Obtain the facetset from the grid
∂Ω = getfacetset(grid, "boundary-1")

# Prescribe scalar field :s on ∂Ω to sin(t)
dbc = Dirichlet(:s, ∂Ω, (x, t) -> sin(t))

# Prescribe all components of vector field :v on ∂Ω to 0
dbc = Dirichlet(:v, ∂Ω, x -> 0 * x)

# Prescribe component 2 and 3 of vector field :v on ∂Ω to [sin(t), cos(t)]
dbc = Dirichlet(:v, ∂Ω, (x, t) -> [sin(t), cos(t)], [2, 3])
```

`Dirichlet` boundary conditions are added to a [`ConstraintHandler`](@ref) which applies the condition via [`apply!`](@ref) and/or [`apply_zero!`](@ref).
