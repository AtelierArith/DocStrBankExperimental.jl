```
evaluation_function(e::NumFieldEmb, prec::Int) -> Function
```

無名関数 `x -> e(x, prec)` を返します。

# 例

```jldoctest
julia> K, a = quadratic_field(-3);

julia> e = complex_embeddings(K)[1];

julia> fn = evaluation_function(e, 64);

julia> fn(a)
[+/- 3.99e-77] + [1.73205080756887729353 +/- 5.41e-21]*im
```
