```
StencilArray <: AbstractStencilArray

StencilArray(A::AbstractArray, stencil::Stencil; kw...)
```

[`Stencil`](@ref) と [`BoundaryCondition`](@ref)、および [`Padding`](@ref) を持つ配列です。

ほとんどの使用法では、`StencilArray` は通常の配列とまったく同じように機能します。

ただし、`stencil` で任意のポイントをインデックス指定して埋められた `Stencil` オブジェクトを返したり、`neighbors` で隣接要素の `SVector` を返したりできます。

## 引数

  * `A`: `AbstractArray`
  * `stencil`: [`Stencil`](@ref)。

## キーワード

  * `boundary`: [`Wrap`](@ref) のような [`BoundaryCondition`](@ref)。デフォルトは `Remove()` です。
  * `padding`: [`Conditional`](@ref) や [`Halo{:in}`](@ref) のような [`Padding`](@ref)。デフォルトは `Conditional()` です。

## 例

```jldoctest
using Stencils, Statistics
sa = StencilArray((1:10) * (10:20)', Moore(1); boundary=Wrap())
sa .*= 2 # ブロードキャストは通常通り機能します
means = mapstencil(mean, sa) # mapstencil は機能します
stencil(sa, 5, 6) # ステンシルを手動で読み取ることもできます

# 出力

Moore{1, 2, 8, Int64}
█▀█
▀▀▀

隣接要素とともに:
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
