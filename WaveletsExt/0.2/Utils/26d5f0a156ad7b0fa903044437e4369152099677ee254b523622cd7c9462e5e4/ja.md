```
coarsestscalingrange(x, tree[, redundant])
coarsestscalingrange(n, tree[, redundant])
```

バイナリツリーを与えると、最も粗いスケーリング係数のインデックス範囲を返します。

# 引数

  * `x::AbstractArray{T} where T<:Number`: 分解された1D信号。
  * `n::Integer`: 興味のある信号の長さ。
  * `tree::BitVector`: バイナリツリー。
  * `redundant::Bool`: (デフォルト: `false`) ウェーブレット分解が冗長であるかどうか。冗長なウェーブレット変換の例には、自己相関ウェーブレット変換 (ACWT)、定常ウェーブレット変換 (SWT)、および最大重複ウェーブレット変換 (MOWT) が含まれます。

# 戻り値

`UnitRange{Integer}` または `::Tuple{UnitRange{Integer}, Integer}`: 入力バイナリツリーに基づく最も粗いスケーリング部分空間のインデックス範囲。

# 例

```@repl
using Wavelets, WaveletsExt

x = randn(8)
wt = wavelet(WT.haar)
tree = maketree(x)

# 非冗長ウェーブレット変換
xw = wpd(x, wt)
coarsestscalingrange(xw, tree)          # 1:1

# 冗長ウェーブレット変換
xw = swpd(x, wt)
coarsestscalingrange(xw, tree, true)    # (1:8, 8)
```

*参照:* [`finestdetailrange`](@ref)
