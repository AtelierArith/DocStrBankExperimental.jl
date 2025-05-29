```
unfussy(measure)
```

引数チェックが削除された `measure` のバージョンを返します。具体的には、`measure == fussy_measure(atomic_measure)` である場合、ある `atomic_measure` に対して、`atomic_measure` を返します。それ以外の場合は、`measure` を返します。

[`StatisticalMeasuresBase.fussy_measure`](@ref) も参照してください。
