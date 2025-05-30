```
keyedreduce(op, key::AbstractVector{T}, a, init=0.0) where T
```

`countmap` に似ており、`key` のユニークなキーをマッピングする辞書を返し、与えられたバイナリ演算子 `op` で与えられたコレクション itr を還元します。

```
julia> keyedreduce(+, [:a, :b, :a], [7, 3, 2])
Dict{Symbol, Float64} with 2 entries:
  :a => 9.0
  :b => 3.0
```
