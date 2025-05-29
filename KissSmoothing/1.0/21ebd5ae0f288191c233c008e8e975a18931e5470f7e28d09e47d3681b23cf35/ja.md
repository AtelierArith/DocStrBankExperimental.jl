```
lsq_denoise(S::AbstractVector{<:Real}; order::Integer=3, strength::Real = NaN)
```

シーケンス S のノイズを除去するために、最小二乗回帰においてその order-th 有限差分にペナルティを課します。

```
`S` : シーケンス。

キーワード引数:

`order` : 有限差分の順序。

`strength` : [0, Inf[ の範囲で導関数に対するペナルティの強度。指定しない場合は自動的に決定されます。
```

フィルタリングされたシーケンスを返します。
