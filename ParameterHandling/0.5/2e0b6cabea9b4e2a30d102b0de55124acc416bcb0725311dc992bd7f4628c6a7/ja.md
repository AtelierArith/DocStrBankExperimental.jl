```
flatten([eltype=Float64], x)
```

`x`の"フラット"な表現を実数のベクトルとして返し、同じ長さの実数のベクトルを受け取り、`x`と同じ型のオブジェクトを返す関数`unflatten`を返します。

`unflatten`は`flatten`の逆ですので、

```julia
julia> x = (randn(5), 5.0, (a=5.0, b=randn(2, 3)));

julia> v, unflatten = flatten(x);

julia> x == unflatten(v)
true
```
