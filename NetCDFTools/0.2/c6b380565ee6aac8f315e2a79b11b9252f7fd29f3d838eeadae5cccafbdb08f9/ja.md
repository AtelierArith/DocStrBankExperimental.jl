```
split_chunk(n::Int, nchunk=4; chunk=nothing, ratio_small::Real=0.5)
```

# 引数

  * `ratio_small`: 最後のチャンクの最小比率をチャンクの最大長さに対して指定します。

最後のブロックがこの比率未満の場合、最後の2つのブロックが結合されます。
