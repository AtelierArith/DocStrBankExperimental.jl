```
idwtall(xw, wt[, L])
```

各信号のスライスに対して逆離散ウェーブレット変換（iDWT）を計算します。信号は、$n$次元入力 `xw` の$n$次元目でスライスされます。

!!! note
    `idwt` は現在、1-D、2-D、および3-D信号のみに対応しています。


# 引数

  * `xw::AbstractArray{T} where T<:Number`: 入力された分解信号で、各スライスは1つの信号に対応します。次元$n$の入力信号 `xw` のセットに対して、信号は$n$次元目でスライスされます。
  * `wt::OrthoFilter`: 使用されるウェーブレット。
  * `L::Integer`: （デフォルト: `Wavelets.maxtransformlevels(xwᵢ)`）ウェーブレット変換のレベル数。

# 戻り値

`::Array{T}`: 再構成された信号のスライス。信号は入力 `xw` と同じ方法でスライスされます。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# xのすべての信号に対してDWT
xw = dwtall(x, wt)

# すべての信号に対してiDWT
x̂ = idwtall(xw, wt)
```

**参照:** [`dwtall`](@ref), [`iwpdall`](@ref), [`iwptall`](@ref) ```
