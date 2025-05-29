```
terms_needed(dim, q_12, stepsize, eps, alg, norm)
```

有限次元のQ-ウィーナー過程の近似に使用され、共分散行列は$Q = Q^\frac{1}{2}*Q^\frac{1}{2}$です。ここで`q_12`は$Q^\frac{1}{2}$の固有値のベクトルであり、共分散行列の平方根です。同様に、これらは$Q$の固有値の平方根です。

# 例

```jldoctest; setup=:(using LevyArea)
julia> h = 1/128;

julia> dim = 10;

julia> q = [1/k^2 for k=1:dim];

julia> terms_needed(dim, sqrt.(q), h, h^(3/2), Milstein(), FrobeniusL2())
9
```
