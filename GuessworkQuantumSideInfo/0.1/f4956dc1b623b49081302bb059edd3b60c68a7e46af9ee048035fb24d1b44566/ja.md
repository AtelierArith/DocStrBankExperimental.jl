```
randprobvec([rng, T=Float64], d)
```

標準の `d-1` 次元単体上で、[Smith and Tromble](http://www.cs.cmu.edu/~nasmith/papers/smith+tromble.tr04.pdf) によるアルゴリズムを使用して、型 `T` の点を一様にランダムに生成します。

## 例

```julia
julia> randprobvec(3)
3-element Array{Float64,1}:
 0.24815974900033688
 0.17199716455672287
 0.5798430864429402 

```
