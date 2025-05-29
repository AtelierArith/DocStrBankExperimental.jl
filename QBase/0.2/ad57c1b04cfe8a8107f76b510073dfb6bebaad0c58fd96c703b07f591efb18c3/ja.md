```
is_hermitian( M :: AbstractMatrix{<:Number}; atol=ATOL :: Float64 ) :: Bool
```

供給された行列がエルミート（自己随伴）である場合は `true` を返します。すなわち、`M == M'` です。
