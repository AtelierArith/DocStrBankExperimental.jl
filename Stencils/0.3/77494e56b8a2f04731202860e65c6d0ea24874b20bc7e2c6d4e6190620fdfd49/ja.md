```
mapstencil(f, A::StencilArray, args::AbstractArray...)
mapstencil(f, stencil::Stencil, A::AbstractArray, args::AbstractArray...; kw...)
```

ステンシルマッピングでは、`f` が `A` の各インデックスで中心にある [`Stencil`](@ref) を受け取り、その後に各ステンシル中心での `args` からの値が続きます。

## キーワード

  * `boundary`: [`Wrap`](@ref) のような [`BoundaryCondition`](@ref)。デフォルトは `Remove()` です。
  * `padding`: [`Conditional`](@ref) や [`Halo{:in}`](@ref) のような [`Padding`](@ref)。デフォルトは `Conditional()` です。

結果は新しい配列として返されます。
