```
LensAssembly{T<:Real}
```

Structure which contains the elements of the optical system, these can be [`CSGTree`](@ref) or [`Surface`](@ref) objects.

In order to prevent type ambiguities bespoke structs are created for each possible number of elements e.g. `LensAssembly3`. These are parameterized by the types of the elements to prevent ambiguities. Basic surface types such as [`Rectangle`](@ref) (which can occur in large numbers) are stored independently in `Vector`s, so type parameters are only needed for CSG objects.

Each struct looks like this:

```julia
struct LensAssemblyN{T,T1,T2,...,TN} <: LensAssembly{T}
    axis::SVector{3,T}
    rectangles::Vector{Rectangle{T}}
    ellipses::Vector{Ellipse{T}}
    hexagons::Vector{Hexagon{T}}
    paraxials::Vector{ParaxialLens{T}}
    E1::T1
    E2::T2
    ...
    EN::TN
end
```

Where `Ti <: Union{Surface{T},CSGTree{T}}`.

To create a LensAssembly object the following functions can be used:

```julia
LensAssembly(elements::Vararg{Union{Surface{T},CSGTree{T},LensAssembly{T}}}; axis = SVector(0.0, 0.0, 1.0)) where {T<:Real}
```
