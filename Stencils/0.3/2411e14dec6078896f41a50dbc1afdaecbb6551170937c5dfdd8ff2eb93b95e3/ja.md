```
Kernel <: AbstractKernelStencil

Kernel(stencil::Stencil, kernel::AbstractArray)
Kernel(f::Function, stencil::Stencil)
```

他のステンシルオブジェクトをラップし、ステンシルと同じ長さと位置のカーネル配列を含みます。ステンシルとカーネルの関数は、[`kernelproduct`](@ref)のように[`mapstencil`](@ref)で使用できます。

関数 `f` を最初の引数として渡すことができ、`map(f, distances(stencil))` でカーネル配列が計算されます。

例として、カーネルは配列と畳み込むことができます。

```julia
using Stencils

# カーネルが畳み込まれるランダム配列を定義
r = rand(1000, 1000)

# カーネル配列を定義
sharpen = [0 -1 0;
           -1 5 -1;
           0 -1 0]

# カーネル配列と同じサイズのステンシルを定義
stencil = Window(1)

# ステンシルとカーネル配列からステンシルカーネルを作成
k = Kernel(stencil, sharpen)

# ランダム配列とカーネルをステンシル配列にラップ
A = StencilArray(r, k)

# `kernelproduct` 関数を使ってカーネルを配列と畳み込むために `mapstencil` を使用します。
# 注意: `kernelproduce` は `Base.dot` に似ていますが、`kernelproduct` 
# は StaticArray の配列を使用でき、まだ機能します（dot は再帰的です）。
mapstencil(kernelproduct, A) 
```
