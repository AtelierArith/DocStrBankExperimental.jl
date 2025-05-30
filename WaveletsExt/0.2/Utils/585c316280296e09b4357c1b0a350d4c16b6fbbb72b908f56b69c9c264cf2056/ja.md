```
finestdetailrange(x, tree[, redundant])
finestdetailrange(n, tree[, redundant])
```

与えられたバイナリツリーに対して、最も細かい詳細係数のインデックス範囲を返します。

# 引数

  * `x::AbstractArray{T} where T<:Number`: 分解された1D信号。
  * `n::Integer`: 興味のある信号の長さ。
  * `tree::BitVector`: バイナリツリー。
  * `redundant::Bool`: (デフォルト: `false`) ウェーブレット分解が冗長であるかどうか。冗長なウェーブレット変換の例には、自己相関ウェーブレット変換 (ACWT)、定常ウェーブレット変換 (SWT)、および最大重複ウェーブレット変換 (MOWT) が含まれます。

# 戻り値

`UnitRange{Integer}` または `::Tuple{UnitRange{Integer}, Integer}`: 入力バイナリツリーに基づく最も細かい詳細サブスペースのインデックス範囲。

# 例

```@repl
using Wavelets, WaveletsExt

x = randn(8)
wt = wavelet(WT.haar)
tree = maketree(x)

# 非冗長ウェーブレット変換
xw = wpd(x, wt)
finestdetailrange(xw, tree)          # 8:8

# 冗長ウェーブレット変換
xw = swpd(x, wt)
finestdetailrange(xw, tree, true)    # (1:8, 15)
```

*参照:* [`coarsestscalingrange`](@ref)
