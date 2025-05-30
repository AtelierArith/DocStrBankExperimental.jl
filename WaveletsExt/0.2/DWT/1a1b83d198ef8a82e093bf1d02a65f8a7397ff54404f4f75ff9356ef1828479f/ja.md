```
iwpd(xw, wt[, L])
iwpd(xw, wt, tree)
```

逆ウェーブレットパケット分解（IWPD）を `L` レベルまたは指定された `tree` に対して計算します。

# 引数

  * `x̂::AbstractVector{T} where T<:Number` または `x̂::AbstractArray{T,2} where T<:Number`: 再構成された信号のための割り当てられた出力ベクトル/行列。
  * `xw::AbstractArray{T,2} where T<:Number` または `xw::AbstractArray{T,3} where T<:Number`: 入力配列。2D入力は1Dウェーブレット再構成を受け、3D入力は2Dウェーブレット再構成を受けます。
  * `wt::OrthoFilter`: ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `minimum(size(x)[1:end-1]) |> maxtransformlevels`）ウェーブレット分解のレベル数。
  * `tree::BitVector`: 逆変換が適切に計算されるためのバイナリツリーまたはクアッドツリー。

# 戻り値

  * `x̂::Array{T,1}` または `x̂::Array{T,2}`: 再構成された信号。

# 例:

```
using Wavelets, WaveletsExt

# 1Dウェーブレット分解
x = randn(8)
wt = wavelet(WT.haar)
xw = wpd(x, wt)

# 1Dウェーブレット再構成
y = iwpd(xw, wt)

# 2Dウェーブレット分解
x = randn(8,8)
wt = wavelet(WT.haar)
xw = wpd(x, wt)

# 2Dウェーブレット再構成
y = iwpd(xw, wt)
```

**参照:** [`iwpd!`](@ref), [`iwpt`](@ref)
