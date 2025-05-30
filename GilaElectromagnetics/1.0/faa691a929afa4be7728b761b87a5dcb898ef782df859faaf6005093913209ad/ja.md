```
GlaOpr(celSrc::NTuple{3, Int}, sclSrc::NTuple{3, Rational}, 
orgSrc::NTuple{3, Rational}, celTrg::NTuple{3, Int}, 
sclTrg::NTuple{3, Rational}, orgTrg::NTuple{3, Rational}; 
useGpu::Bool=false, setTyp::DataType=ComplexF64)
```

外部グリーン演算子を構築します。

# 引数

  * `celSrc::NTuple{3, Int}`: ソースボリュームの各次元のセルの数。
  * `sclSrc::NTuple{3, Rational}`: ソースボリュームの各次元の各セルのサイズ（波長の単位）。
  * `orgSrc::NTuple{3, Rational}`: ソースボリュームの各次元の原点（波長の単位）。
  * `celTrg::NTuple{3, Int}`: ターゲットボリュームの各次元のセルの数。
  * `sclTrg::NTuple{3, Rational}`: ターゲットボリュームの各次元の各セルのサイズ（波長の単位）。
  * `orgTrg::NTuple{3, Rational}`: ターゲットボリュームの各次元の原点（波長の単位）。
  * `useGpu::Bool=false`: GPUを使用するかどうか（true）またはCPUを使用するか（false）。
  * `setTyp::DataType=ComplexF64`: 演算子の要素タイプ。`Complex`のサブタイプでなければなりません。
