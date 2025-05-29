```
ttsvd(red_style::TTSVDRanks,A::AbstractArray) -> AbstractVector{<:AbstractArray}
ttsvd(red_style::TTSVDRanks,A::AbstractArray,X::AbstractRankTensor) -> AbstractVector{<:AbstractArray}
```

`A`のテンソル列SVD。提供される場合、`X`は出力が直交するようにするノルムテンソル（対称かつ正定値行列を表す）です。注意: `ndims(A)` = N の場合、出力の長さは `N-1` です。パラメータの軸を削減することには興味がないためです。詳細については、[こちら](https://arxiv.org/abs/2412.14460)の参考文献を確認してください。
