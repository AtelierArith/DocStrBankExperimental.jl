```
laplace(f, x)
```

フィールド `f` のラプラシアンを点 `x` で計算します。`f` がベクトル場の場合は、ブロードキャスティングを使用してください。

# 例

```jldoctest
julia> x = rand(Vec{3});

julia> f(x) = norm(x);

julia> laplace(f, x)
2.9633756571179273

julia> g(x) = x*norm(x);

julia> laplace.(g, x)
3-element Vec{3, Float64}:
 1.9319830062026155
 3.2540895437409754
 1.2955087437219237
```
