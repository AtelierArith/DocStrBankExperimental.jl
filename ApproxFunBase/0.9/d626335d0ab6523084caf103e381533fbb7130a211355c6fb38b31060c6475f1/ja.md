```
Fun(f)
```

関数のために適切な `space` を選択することによって `Fun(f, space)` を返します。単変数関数の場合、`space` は `Chebyshev()` に選ばれ、多変数関数の場合は `Chebyshev()` 空間のテンソル積になります。

# 例

```jldoctest
julia> f = Fun(x -> x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> f(0.1) == (0.1)^2
true

julia> f = Fun((x,y) -> x + y);

julia> f(0.1, 0.2) ≈ 0.3
true
```
