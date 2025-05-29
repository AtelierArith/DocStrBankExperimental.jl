```
iswpd(xw, wt, L, sm)
iswpd(xw, wt[, L])
iswpd(xw, wt, tree[, sm])
```

`xw`に対して逆定常ウェーブレットパケット変換（iSWPT）を計算します。

!!! note
    この関数は、生の分解信号を再構築しようとしている場合にはあまり役に立たないかもしれません。この関数の目的は、信号が分解（`swpd`）され、しきい値処理（`denoise`/`denoiseall`）された後に再構築されるようなアプリケーションでより良く活用されるでしょう。


# 引数

  * `xw::AbstractArray{T,2}` または `x::AbstractArray{T,3} where T<:Number`: SWPD変換された配列。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `maxtransformlevels(x)` または `minimum(size(xw)[1:end-1]) |> maxtransformlevels`）再構築に使用される分解のレベル数。
  * `tree::BitVector`: 逆変換が適切に計算されるためのバイナリ/クアッドツリー。
  * `sm::Integer`: `sm`が引数として含まれている場合、`sm`シフトされた逆変換が計算されます。これにより計算が大幅に高速化されますが、冗長なウェーブレット変換の強みを完全には活用できません。

# 戻り値

`::Vector{T}` または `::Matrix{T}`: 逆変換された信号。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPD
xw = swpt(x, wt)

# シフトベースのiSWPD
x̂ = iswpd(xw, wt, maxtransformlevels(xw,1), 5)

# 平均ベースのiSWPD
x̃ = iswpd(xw, wt)
```

**関連項目:** [`isdwt_step`](@ref), [`iswpt`](@ref), [`swpd`](@ref), [`iswpd!`](@ref)
