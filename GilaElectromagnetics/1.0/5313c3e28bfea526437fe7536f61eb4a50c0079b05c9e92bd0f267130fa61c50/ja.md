```
GlaOpr(cel::NTuple{3, Int}, scl::NTuple{3, Rational}, 
org::NTuple{3, Rational}=(0//1, 0//1, 0//1); 
useGpu::Bool=false, setTyp::DataType=ComplexF64)
```

自己グリーン演算子を構築します。

# 引数

  * `cel::NTuple{3, Int}`: 各次元のセルの数。
  * `scl::NTuple{3, Rational}`: 各次元の各セルのサイズ

（波長の単位で）。

  * `org::NTuple{3, Rational}=(0//1, 0//1, 0//1)`: 各次元の体積の原点

（波長の単位で）。

  * `useGpu::Bool=false`: GPUを使用するかどうか（true）またはCPU（false）。
  * `setTyp::DataType=ComplexF64`: 演算子の要素タイプ。`Complex`の

サブタイプでなければなりません。
