```
getbasiscoef(Xw, tree)
```

分解された信号 `Xw` に対する基底係数をツリー `tree` に関して取得します。

# 引数

  * `Xw::AbstractArray{T,2} where T<:Number`: 分解された1次元信号。
  * `tree::BitVector`: 対応する基底ツリー。

# 戻り値

  * `::Array{T,1}`: 信号の基底係数。

# 例

```julia
using Wavelets, WaveletsExt

# 信号とウェーブレットを生成
x = generatesignals(:heavysine)
wt = wavelet(WT.db4)

# 信号を分解
Xw = iwpd(x, wt)
tree = maketree(128, 6, :dwt)

# 基底係数を取得
xw = getbasiscoef(Xw, tree)
```
