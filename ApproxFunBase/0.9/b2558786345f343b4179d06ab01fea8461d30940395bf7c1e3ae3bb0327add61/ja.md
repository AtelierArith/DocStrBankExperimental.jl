```
DefiniteIntegral([sp::Space])
```

定義された積分を返します。`Fun`をその定義域で積分します。`sp`が指定されていない場合、実行時にコンテキストから推測されます。

# 例

```jldoctest
julia> f = Fun(x -> 3x^2, Chebyshev());

julia> DefiniteIntegral() * f ≈ 2 # -1..1の範囲での3x^2の積分
true
```
