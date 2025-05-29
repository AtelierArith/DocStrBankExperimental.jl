```
近傍
```

近傍は、現在のセルの「近傍」における周囲のセルのパターンを定義します。`neighbors`関数は、周囲のセルを反復可能な形で返します。

主な種類の近傍は以下に示されています：

![近傍](https://raw.githubusercontent.com/cesaraustralia/DynamicGrids.jl/media/Neighborhoods.png)

近傍は`NeighborhoodRule`および`SetNeighborhoodRule`で使用されます - 同じ形状ですが異なる目的があります。`NeighborhoodRule`では、近傍は`neighbors`関数から反復可能な形で返される現在のセルの周囲のセルを指定します。これらはカウント、合計、比較、または`AbstractKernelNeighborhood`内のカーネルと掛け算することができます。[`kernelproduct`](@ref)を使用します。

`SetNeighborhoodRule`では、近傍は中央のセルの周囲のセルの位置を、各近傍のインデックスの周りの[`offsets`]および絶対[`positions`](@ref)として提供します。これらは手動で書き込むことができます。
