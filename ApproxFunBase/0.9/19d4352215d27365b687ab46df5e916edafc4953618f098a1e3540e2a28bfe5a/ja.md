```
coefficients(f::Fun, s::Space) -> Vector
```

関数 `f` の係数を空間 `s` で返します。`s` は `space(f)` と同じでない場合があります。

# 例

```jldoctest
julia> f = Fun(x->(3x^2-1)/2);

julia> coefficients(f, Legendre()) ≈ [0, 0, 1]
true
```
