```
mapstencil!(f, dest::AbstractArray, source::StencilArray, args::AbstractArray...)
mapstencil!(f, A::SwitchingStencilArray, args::AbstractArray...)
```

Stencil mapping where `f` is passed a stencil centered at each index in `src`, followed by the values from `args` at each stencil center. The result of `f` is written to `dest`.

For SwitchingStencilArray the internal source and dest arrays are used, returning a switched version of the array.

`dest` must either be smaller than `src` by the stencil radius on all sides, or be the same size, in which case it is assumed to also be padded.
