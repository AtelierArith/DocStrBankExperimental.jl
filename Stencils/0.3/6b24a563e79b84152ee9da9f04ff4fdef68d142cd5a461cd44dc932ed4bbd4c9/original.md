```
SwitchingStencilArray <: AbstractSwitchingStencilArray

SwitchingStencilArray(A::AbstractArray, stencil; 
    boundary=Remove(zero(eltype(parent))),
    padding=Conditional(),
)
```

An `AbstractArray` with a [`Stencil`](@ref), a [`BoundaryCondition`](@ref), [`Padding`](@ref), and two array layers that are switched with each `broadcast_stencil` operation.

The use case for this operation is in simulations where stencil operations are repeatedly run over the same data, or where a filter (such as a blur) needs to be applied many times.

For most uses a `SwitchingStencilArray` works exactly the same as a regular array - the `dest` array can be safely ignored.

However, when using `mapstencil!` you need to use the output, not the original array. Switching does not happen in-place, but as a new returned array.

## Arguments

  * `A`: an `AbstractArray`
  * `stencil`: a [`Stencil`](@ref).

## Keywords

  * `boundary`: a [`BoundaryCondition`](@ref) like [`Wrap`](@ref). `Remove()` is the default.
  * `padding`: [`Padding`](@ref) like [`Conditional`](@ref) or [`Halo{:in}`](@ref). `Conditional()` is the default.

## Example

```jldoctest
using Stencils, Statistics

sa = SwitchingStencilArray(rand(10, 10), Moore(1); boundary=Wrap())
sa .*= 2 # Broadcast works as usual
mapstencil(mean, sa) # As does runing `mapstencils
s = stencil(sa, 5, 10) # And retreiving a single stencil
# But we can also run it in-place, here doing 10 iterations of mean blur:
# Note: if you dont assign new variable with `A =`, the array will
# not switch and will not be blurred.
let sa = sa
    for i in 1:10
        sa = mapstencil!(mean, sa)
    end
end
# output

```
