```
bboptimize(problem[, x0, parameters::Associative; kwargs...])
```

与えられた最適化 `problem` を解決します。オプションで、開始点 `x0` を指定できます。

サポートされている `problem` のタイプについては `setup_problem()` を参照してください。さらに、`problem` は以前の最適化実行の結果を含む `OptController` である可能性があります。

最適化手法のパラメータは `kwargs` または `parameters` 引数を介して指定できます。

`OptimizationResults` インスタンスを返します。

サポートされているパラメータの完全なリストについては、`bbsetup()` および [`BlackBoxOptim.OptRunController`](@ref) を参照してください。
