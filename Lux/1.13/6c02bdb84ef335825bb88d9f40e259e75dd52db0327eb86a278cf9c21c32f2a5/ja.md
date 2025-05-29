```
FlattenLayer(; N = nothing)
```

渡された配列を行列にフラット化します。

## キーワード引数

  * `N`: 入力配列の最初の `N` 次元をフラット化します。`nothing` の場合、すべての次元（最後の次元を除く）がフラット化されます。バッチ次元は決してフラット化されないことに注意してください。

## 入力

  * `x`: AbstractArray

## 戻り値

  * `N` が `nothing` の場合はサイズ `(:, size(x, ndims(x)))` の AbstractMatrix、そうでない場合は入力配列の最初の `N` 次元がフラット化されます。
  * 空の `NamedTuple()`

## 例

```jldoctest
julia> model = FlattenLayer()
FlattenLayer{Nothing}(nothing)

julia> rng = Random.default_rng();
       Random.seed!(rng, 0);
       ps, st = Lux.setup(rng, model);
       x = randn(rng, Float32, (2, 2, 2, 2));

julia> y, st_new = model(x, ps, st);
       size(y)
(8, 2)
```
