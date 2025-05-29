```
Convolution <: NeighborhoodRule

Convolution(kernel::AbstractArray)
Convolution{R,W}(kernel::AbstractArray)
```

グリッド上で畳み込みカーネルを実行する [`NeighborhoodRule`](@ref) です。

`kernel` は正方行列でなければなりません。

## パフォーマンス

DynamicGrids.jl における小半径の畳み込みは、DSP.jl や ImageConvolutions.jl を使用するよりも同等か、さらには速くなるでしょう。半径が大きくなるにつれて、これらのパッケージははるかに速くなります。

しかし、`Convolution` はシミュレーションに連鎖させるのに便利で、他のいくつかのルールと組み合わせることができます。非常に大きなカーネルを除いて、すべてのカーネルで合理的に良好なパフォーマンスを発揮するはずです。

値は正規化されていないため、必要な場合はカーネルの合計が `1` になるようにしてください。

## 例

砂が吹き飛ばされるように見えるストリーキング畳み込み。

パターンを変更するために行列の値を入れ替えてください。

```julia
using DynamicGrids, DynamicGridsGtk
streak = Convolution([0.0 0.01 0.48; 
                      0.0 0.5  0.01; 
                      0.0 0.0  0.0])
output = GtkOutput(rand(500, 500); tspan = 1:1000, fps=100)
sim!(output, streak; boundary=Wrap())
```
