```
outputsize(m, inputsize::Tuple; padbatch=false)
```

モデル `m` の出力サイズを、入力のサイズに基づいて計算します。これは、正しい入力 `x` に対して `outputsize(m, size(x)) == size(m(x))` に従います。

キーワード `padbatch=true` は `(inputsize..., 1)` を使用するのと同等で、この追加のバッチ次元を含む最終サイズを返します。

これは `size(m(x))` を呼び出すよりも速いはずです。カスタムレイヤーに対してもそのまま動作するはずのトリビアルな数値型を使用します。

`m` が `Tuple` または `Vector` の場合、その要素は `Chain(m...)` のように順番に適用されます。

# 例

```jldoctest
julia> using Flux: outputsize

julia> outputsize(Dense(10 => 4), (10,); padbatch=true)
(4, 1)

julia> m = Chain(Conv((3, 3), 3 => 16), Conv((3, 3), 16 => 32));

julia> m(randn(Float32, 10, 10, 3, 64)) |> size
(6, 6, 32, 64)

julia> outputsize(m, (10, 10, 3); padbatch=true)
(6, 6, 32, 1)

julia> outputsize(m, (10, 10, 3, 64))
(6, 6, 32, 64)

julia> try outputsize(m, (10, 10, 7, 64)) catch e println(e) end
DimensionMismatch("layer Conv((3, 3), 3 => 16) expects size(input, 3) == 3, but got 10×10×7×64 Array{Flux.NilNumber.Nil, 4}")

julia> outputsize([Dense(10 => 4), Dense(4 => 2)], (10, 1)) # レイヤーのベクターは Chain になります
(2, 1)
```
