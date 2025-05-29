```
lc_eltype(o) ≡ eltype
```

コレクションの最小共通 eltype。

#### 例:

```
julia> o = ([1//2, 1//3]; (1//4, 1//1, 1//6));
julia> lc_eltype(o)
Rational{Int64}

julia> o = ([1//2, 1//3]; (1//4, big(1)//big(5), 1//6));
julia> lc_eltype(o)
Rational

julia> o = ([1//2, 1//3]; (1//4, [big(1)//big(5)], 1//6));
julia> lc_eltype(o)
Any

julia> o = ([1/2, 1/3]; (1/4, 1/1, 1/6));
julia> lc_eltype(o)
Float64
```
