```
prime_decomposition_type(O::AbsSimpleNumFieldOrder, p::Integer) -> Vector{Tuple{Int, Int}}
```

$$
p
$$

の上にある素数の数だけの長さを持つタプルの配列を返し、$i$-番目のタプルは対応する素数の分裂型を示し、慣性次数と分岐指数の順に並んでいます。
