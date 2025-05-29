```
mapstencil(f, A::StencilArray, args::AbstractArray...)
mapstencil(f, stencil::Stencil, A::AbstractArray, args::AbstractArray...; kw...)
```

Stencil mapping where `f` is passed a [`Stencil`](@ref) centered at each index in `A`, followed by the values from `args` at each stencil center.

## Keywords

  * `boundary`: a [`BoundaryCondition`](@ref) like [`Wrap`](@ref). `Remove()` is the default.
  * `padding`: [`Padding`](@ref) like [`Conditional`](@ref) or [`Halo{:in}`](@ref). `Conditional()` is the default.

The result is returned as a new array.
