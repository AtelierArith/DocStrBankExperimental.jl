```
relerrorthreshold(coef, [redundant, tree, elbows; makeplot])
```

展開係数のセットを受け取り、しきい値と相対誤差の曲線を「プロット」し、エルボー法に基づいて最適なしきい値を選択します。この計算から得られたプロットを見たい場合は、単に `makeplot=true` に設定してください。

# 引数

  * `coef::AbstractArray{T} where T<:Number`: 分解された信号。
  * `redundant::Bool`: (デフォルト: `false`) `xw` の変換タイプが冗長変換であるかどうか。自己相関や定常ウェーブレット変換は冗長変換の例です。
  * `tree::Union{BitVector, Nothing}`: (デフォルト: `nothing`) `xw` を分解するための基底ツリー。`xw` が `swdp` または `acwpd` を使用して分解される場合は提供する必要があります。
  * `elbows::Integer`: (デフォルト: 2) 最適なしきい値を決定するために使用されるエルボーの数。

# キーワード引数

  * `makeplot::Bool`: (デフォルト: `false`) 最適なしきい値を決定するために使用されたプロットを返すかどうか。

# 戻り値

  * `::AbstractFloat`: 最適なしきい値。
  * `::GR.Plot`: 最適なしきい値を決定するために使用されたプロット。`makeplot = true` の場合のみ返されます。

# 例

```julia
x = randn(128)
wt = wavelet(WT.haar)

# dwt変換のためのノイズ推定
y = dwt(x, wt)
noise = relerrorthreshold(y, false)

# wpt変換のためのノイズ推定
tree = maketree(x, :full)
y = wpt(x, wt, tree)
noise = relerrorthreshold(y, false, tree)

# sdwt変換のためのノイズ推定
y = sdwt(x, wt)
noise = relerrorthreshold(y, true)

# swpd変換のためのノイズ推定
y = swpd(x, wt)
noise = relerrorthreshold(y, true, tree)
```

**参照:** [`noisest`](@ref), [`RelErrorShrink`](@ref)
