```
scale(λ::Int,Ω::UnitRange{Int})
```

範囲スケーリング。

**注意:**

Juliaの`*`演算子はステップ範囲を返すため、使用しません：

```jldoctest
julia> r=6:8
6:8

julia> -2*r
-12:-2:-16
```

私たちが必要とするのは：

```jldoctest
julia> r=6:8
6:8

julia> scale(-2,r)
-16:-12
```
