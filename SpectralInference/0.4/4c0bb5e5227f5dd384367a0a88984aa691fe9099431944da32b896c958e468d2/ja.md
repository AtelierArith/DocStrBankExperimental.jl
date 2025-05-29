```
empiricalMI(a::AbstractVector{<:Float}, b::AbstractVector{<:Float}[, nbins=50, normalize=false])
```

は、$H(a) + H(b) - H(a,b)$の同一性から経験的MIを計算します。ここで、$H := -sum(p(x)*log(p(x))) + log(Δ)$であり、$+ log(Δ)$はログビン幅に対応し、ビン幅の選択からエントロピー推定をバイアスなしにします。推定値は、$32$（$32^2 ≈ 1000$の合計ビン）からサンプルサイズまでおおよそ安定しています。その範囲内で小さな過小評価から小さな過大評価に移行します。`nbins`引数には`sqrt(mean(1000, samplesize))`を選択するか、その範囲内でいくつかの推定を行い平均を取ることをお勧めします。

Args:

  * a, 長さNのベクトル
  * b, 長さNのAbstractVector
  * nbins, 各側のビンの数、最良の結果を得るために1000 < nbins^2 < length(a)を使用
  * base, MIの基本単位（デフォルトはnatsでbase=ℯ）
  * normalize, bool, mi / mean(ha, hb)で正規化するかどうか

Returns:

  * MI
