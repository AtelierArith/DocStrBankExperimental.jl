```
excess_solution_check!(path_result::PathResult,
                       F::RandomizedSystem,
                       newton_cache = NewtonCache(F.system))
```

[`PathResult`](@ref) `path_result` に、`path_result` がランダム化システム `F` の解であるが、`F` の基礎となる多項式システムの解ではない場合、`return_code` `:excess_solution` を割り当てます。これは、非特異解に対してニュートン法を使用し、特異解の解の残差を比較することによって行われます。
