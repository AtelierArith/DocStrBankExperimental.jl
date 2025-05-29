```
cache = LineSearchCache{T}()
```

ラインサーチ中に中間結果を保存するための空のキャッシュを初期化します。ラインサーチ中に計算された `α`、`ϕ(α)`、およびおそらく `dϕ(α)` の値は、それぞれ `cache.alphas`、`cache.values`、および `cache.slopes` で利用可能です。

# 例

```jldoctest
julia> ϕ(x) = (x - π)^4; dϕ(x) = 4*(x-π)^3;

julia> cache = LineSearchCache{Float64}();

julia> ls = BackTracking(; cache);

julia> ls(ϕ, 10.0, ϕ(0), dϕ(0))
(1.8481462933284658, 2.7989406670901373)

julia> cache
LineSearchCache{Float64}([0.0, 10.0, 1.8481462933284658], [97.40909103400242, 2212.550050116452, 2.7989406670901373], [-124.02510672119926])
```

`BackTracking` は `α=0` の場合を除いて導関数を使用しないため、初期の傾きのみがキャッシュに保存されました。他のメソッドは三つすべてを保存する場合があります。
