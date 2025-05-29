```
fussy_measure(measure; extra_check=nothing)
```

新しい測定値 `fussy` を返します。これは `measure` と同じ動作をしますが、データに対して `fussy` を呼び出すか、`fussy` とデータに対して `measuremnts` を呼び出すと、以下の追加チェックが行われます：

  * `weights` または `class_weights` が指定されている場合、`measure` がそれらをサポートしていることを確認します（[`StatisticalMeasuresBase.check_weight_support`](@ref) を参照）。
  * `ŷ`（予測されたプロキシ）、`y`（真の値）、`weights` および `class_weights` が、観測数とクラスプールの観点から互換性があることを確認します（関連する場合は、[`StatisticalMeasuresBase.check_numobs`](@ref) および [`StatisticalMeasuresBase.check_pools`](@ref) を参照）。
  * `extra_check(measure, ŷ, y[, weights, class_weights])` を呼び出します。ただし、`extra_check==nothing` の場合は除きます。ここでの最初の引数は `measure` であり、`atomic_measure` ではありません。

`y` と `ŷ` の両方が MLUtils.jl の `getobs`/`numobs` インターフェースを実装することが期待される場合（例：`AbstractArray` である場合）を除いて、`fussy_measure` を使用しないでください。

他にも [`StatisticalMeasuresBase.measurements`](@ref)、[`StatisticalMeasuresBase.is_measure`](@ref) を参照してください。
