```
Fun(f, s::Space)
```

空間 `s` における関数、数、またはベクトル `f` を表す `Fun` を返します。 `f` がベクトル値の場合、`s` のベクトル値の類似物を返します。

# 例

```jldoctest
julia> f = Fun(x->x^2, Chebyshev())
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> f(0.1) == (0.1)^2
true
```
