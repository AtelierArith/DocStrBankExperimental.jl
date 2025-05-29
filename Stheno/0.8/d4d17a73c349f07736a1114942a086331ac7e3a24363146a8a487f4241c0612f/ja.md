```
GPPPInput(p, x::AbstractVector)
```

GPPPの入力のコレクションです。`p`は、ベクトル`x`がどのプロセスから抽出されるべきかを示します。`p`の必要な型は、インデックスされた`GPPP`のキーの型によって決まります。

```jldoctest
julia> x = [1.0, 1.5, 0.3];

julia> v = GPPPInput(:a, x)
3-element GPPPInput{Symbol, Float64, Vector{Float64}}:
 (:a, 1.0)
 (:a, 1.5)
 (:a, 0.3)

julia> v isa AbstractVector{Tuple{Symbol, Float64}}
true

julia> v == map(x_ -> (:a, x_), x)
true
```
