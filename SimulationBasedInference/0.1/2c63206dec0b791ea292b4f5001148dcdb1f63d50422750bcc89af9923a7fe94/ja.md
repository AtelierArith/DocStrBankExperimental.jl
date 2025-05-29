```
from_moments(::Type{T}, mean, stddev) where {T<:Distribution}
```

モーメント法を使用してタイプ `T` の分布を構築します。与えられた `mean` が分布の未変換サポート内にあると仮定します。
