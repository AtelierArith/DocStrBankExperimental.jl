```
matching_map(b₊::AbstractArray, b₋::AbstractArray, matcher::MatchByBasinOverlap)
```

`matching_map` の特別なケースで、IDを値にマッピングする辞書の代わりに、魅力的な盆地を表す `Array` を入力として持ち、その要素がIDです。

マッチングの仕組みについては [`MatchByBasinOverlap`](@ref) を参照してください。
