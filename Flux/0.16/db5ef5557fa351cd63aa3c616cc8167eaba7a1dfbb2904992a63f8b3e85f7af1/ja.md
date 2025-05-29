```
outputsize(m, x_size, y_size, ...; padbatch=false)
```

モデルまたはレイヤー `m` が複数の配列を入力として受け入れる場合、これは `size(m((x, y, ...)))` を返します。ここで `size_x = size(x)` などです。

# 例

```jldoctest
julia> x, y = rand(Float32, 5, 64), rand(Float32, 7, 64);

julia> par = Parallel(vcat, Dense(5 => 9), Dense(7 => 11));

julia> Flux.outputsize(par, (5, 64), (7, 64))
(20, 64)

julia> m = Chain(par, Dense(20 => 13), softmax);

julia> Flux.outputsize(m, (5,), (7,); padbatch=true)
(13, 1)

julia> par(x, y) == par((x, y)) == Chain(par, identity)((x, y))
true
```

`Chain` は複数の配列をタプルとしてのみ受け入れることに注意してください。一方、`Parallel` はそれらを複数の引数としても受け入れます。`outputsize` は常にタプルを提供します。
