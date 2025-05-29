```
ReshapeLayer(dims)
```

渡された配列を `(dims..., :)` のサイズに再形成します。

## 引数

  * `dims`: 配列の新しい次元（最後の次元を除く）。

## 入力

  * `x`: 任意の形状の AbstractArray で、`(dims..., size(x, ndims(x)))` に再形成可能。

## 戻り値

  * サイズが `(dims..., size(x, ndims(x)))` の AbstractArray
  * 空の `NamedTuple()`

## 例

```jldoctest
julia> model = ReshapeLayer((2, 2))
ReshapeLayer(output_dims = (2, 2, :))

julia> rng = Random.default_rng();
       Random.seed!(rng, 0);
       ps, st = Lux.setup(rng, model);
       x = randn(rng, Float32, (4, 1, 3));

julia> y, st_new = model(x, ps, st);
       size(y)
(2, 2, 3)
```
