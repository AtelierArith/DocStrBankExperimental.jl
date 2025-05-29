```
values_excursion(parameters...; kwargs...)
```

これは各パラメータの最初の選択から始まります。各パラメータを一度にその可能な値を通じて変化させることによってテストケースを作成します。

# 例

```julia
values_excursion([:a, :b, :c], [1, 2, 3])
```

参照: [`all_tuples`](@ref)
