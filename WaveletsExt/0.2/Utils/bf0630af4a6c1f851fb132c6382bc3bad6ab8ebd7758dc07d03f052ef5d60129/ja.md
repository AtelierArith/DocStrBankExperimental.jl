```
getbasiscoefall(Xw, tree)
```

`Xw`のすべての分解された信号に対する基底係数を、木`tree`に関して取得します。

# 引数

  * `Xw::AbstractArray{T,3} where T<:Number`: 分解された1D信号のセット。
  * `tree::BitVector` または `tree::BitArray{2}`: 対応する基底木。入力が`BitMatrix`の場合、各列は`Xw`の信号に対応し、したがって列の数は信号の数と等しくなければなりません。

# 戻り値

  * `::Array{T,2}`: 信号の基底係数。

# 例

```julia
using Wavelets, WaveletsExt

# 信号とウェーブレットを生成
c = ClassData(:cbf, 10, 10, 10)
X = generateclassdata(c)
wt = wavelet(WT.db4)

# 信号を分解
Xw = iwpdall(X, wt)
tree = maketree(128, 6, :dwt)

# 基底係数を取得
getbasiscoefall(Xw, tree)
```
