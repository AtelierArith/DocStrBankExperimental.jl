```
setexperiment!(x[, i], value)
```

`MultiAssayExperiment` `x` の実験 `i` を `SummarizedExperiment` `value` に設定します。これにより、変更された `x` への参照が返されます。

`i` は正の整数である場合、`experiments(x)` の長さ以下である必要があります。また、`x` 内の新しいまたは既存の実験を指定する文字列である場合もあります。省略した場合は、デフォルトで最初の実験が設定されます。

# 例

```jldoctest
julia> using MultiAssayExperiments;

julia> x = MultiAssayExperiments.exampleobject();

julia> size(experiment(x, 2))
(50, 8)

julia> val = experiment(x);

julia> setexperiment!(x, 2, val);

julia> size(experiment(x, 2))
(100, 10)
```
