```
StencilArray <: AbstractStencilArray

StencilArray(A::AbstractArray, stencil::Stencil; kw...)
```

An array with a [`Stencil`](@ref) and a [`BoundaryCondition`](@ref), and [`Padding`](@ref).

For most uses a `StencilArray` works exactly the same as a regular array.

Except it can be indexed at any point with `stencil` to return a filled `Stencil` object, or `neighbors` to return an `SVector` of neighbors.

## Arguments

  * `A`: an `AbstractArray`
  * `stencil`: a [`Stencil`](@ref).

## Keywords

  * `boundary`: a [`BoundaryCondition`](@ref) like [`Wrap`](@ref). `Remove()` is the default.
  * `padding`: [`Padding`](@ref) like [`Conditional`](@ref) or [`Halo{:in}`](@ref). `Conditional()` is the default.

## Example

```jldoctest
using Stencils, Statistics
sa = StencilArray((1:10) * (10:20)', Moore(1); boundary=Wrap())
sa .*= 2 # Broadcast works as usual
means = mapstencil(mean, sa) # mapstencil works
stencil(sa, 5, 6) # manually reading a stencil works too

# output

Moore{1, 2, 8, Int64}
█▀█
▀▀▀

with neighbors:
8-element StaticArraysCore.SVector{8, Int64} with indices SOneTo(8):
 112
 140
 168
 120
 180
 128
 160
 192
```
