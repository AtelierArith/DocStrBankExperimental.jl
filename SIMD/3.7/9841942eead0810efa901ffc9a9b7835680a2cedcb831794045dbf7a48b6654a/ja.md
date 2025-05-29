```
VecRange{N}(i::Int)
```

`UnitRange`に類似していますが、インデックス`i`で幅`N`のSIMDベクターをロードするためのものです。

# 例

```jldoctest
julia> xs = ones(4);
julia> xs[VecRange{4}(1)]  # `vload(Vec{4,Float64}, xs, 1)`を呼び出します
<4 x Float64>[1.0, 1.0, 1.0, 1.0]
```
