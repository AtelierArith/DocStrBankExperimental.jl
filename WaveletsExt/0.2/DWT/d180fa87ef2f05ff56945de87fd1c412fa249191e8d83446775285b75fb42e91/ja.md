```
wpd!(y, x, wt[, L])
```

`wpd`と同様ですが、配列の割り当ては行いません。

# 引数

  * `y::AbstractArray{T,2} where T<:Number` または `y::AbstractArray{T,3} where T<:Number`: `x`の出力を書き込むための割り当て済み配列。
  * `x::AbstractVector{T} where T<:Number` または `x::AbstractArray{T,2} where T<:Number`: 入力ベクトル/行列。ベクトル入力は1Dウェーブレット分解を受け、行列入力は2Dウェーブレット分解を受けます。
  * `wt::OrthoFilter`: ウェーブレットフィルタ。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) ウェーブレット分解のレベル数。

# 戻り値

  * `y::AbstractArray{T,2} where T<:Number` または `y::AbstractArray{T,3} where T<:Number`: 分解された信号。入力ベクトルの場合、出力は各列が分解のレベルに対応する2D行列です。入力行列の場合、出力は各スライスが分解のレベルに対応する3D配列です。

# 例:

```
using Wavelets, WaveletsExt

# 1Dウェーブレット分解
x = randn(8)
xw = Array{eltype(x)}(undef, (8,3))
wt = wavelet(WT.haar)
wpd!(xw, x, wt)

# 2Dウェーブレット分解
x = randn(8,8)
xw = Array{eltype(x)}(undef, (8,8,3))
wt = wavelet(WT.haar)
wpd!(xw, x, wt)
```

**関連情報:** [`wpd`](@ref), [`iwpd`](@ref)
