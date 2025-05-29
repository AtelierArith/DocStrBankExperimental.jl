```
benchmark_model(model::Turing.Model; suite_kwargs..., kwargs...)
```

`model`のベンチマークスイートを作成して実行します。

ベンチマークスイートは[`make_turing_suite`](@ref)を使用して作成されます。利用可能なキーワード引数や詳細については[`make_turing_suite`](@ref)を参照してください。

# キーワード引数

  * `suite_kwargs`: [`make_turing_suite`](@ref)に渡されるキーワード引数。
  * `kwargs`: `BenchmarkTools.run`に渡されるキーワード引数。
