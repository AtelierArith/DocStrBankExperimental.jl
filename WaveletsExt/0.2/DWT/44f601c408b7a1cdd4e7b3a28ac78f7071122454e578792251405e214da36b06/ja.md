```
wpd(x, wt[, L])
```

入力信号 x の L レベルのウェーブレットパケット分解 (WPD) を返します。

# 引数

  * `x::AbstractVector{T} where T<:Number` または `x::AbstractArray{T,2} where T<:Number`: 入力ベクトル/行列。ベクトル入力は 1D ウェーブレット分解を受け、行列入力は 2D ウェーブレット分解を受けます。
  * `wt::OrthoFilter`: ウェーブレットフィルター。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) ウェーブレット分解のレベル数。

# 返り値

  * `::Array{T,2}` または `::Array{T,3}`: 分解された信号。入力ベクトル `x` の場合、出力は各列が分解のレベルに対応する 2D 行列です。入力行列 `x` の場合、出力は各スライスの次元 3 が分解のレベルに対応する 3D 配列です。

# 例:

```julia
using Wavelets, WaveletsExt

# 1D ウェーブレット分解
x = randn(8)
wt = wavelet(WT.haar)
xw = wpd(x, wt)

# 2D ウェーブレット分解
x = randn(8,8)
wt = wavelet(WT.haar)
xw = wpd(x, wt)
```

**参照:** [`wpd!`](@ref), [`iwpd`](@ref)
