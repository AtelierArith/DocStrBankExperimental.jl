```
CircularConvolution{M, N, T}
```

M × N 行列のデータ型 T の事前計画された円形畳み込み演算子

# フィールド

  * `Ĝ`: 畳み込みカーネルのDFT係数
  * `F`: 事前計画されたrFFT演算子
  * `F⁻¹`: 事前計画されたirFFT演算子
  * `nthreads` : 適切な場合に使用する最適化されたスレッド数
  * `paddedSpace`: 入力行列をゼロパディングするためのスクラッチスペース
  * `Â`: ゼロパディングされた入力行列のDFT係数を保存するためのスクラッチスペース

# コンストラクタ:

  * `CircularConvolution(G::Matrix{T})`

# 例:

```jldoctest
julia> G = repeat(1.0:3,1,4)
3×4 Array{Float64,2}:
 1.0  1.0  1.0  1.0
 2.0  2.0  2.0  2.0
 3.0  3.0  3.0  3.0

julia> C = CircularConvolution(G)
Circular convolution on a 3 × 4 matrix of data type Float64

julia> C*reshape(1:12, 3, 4)
3×4 Array{Int64,2}:
 164  164  164  164
 130  130  130  130
 148  148  148  148
```
