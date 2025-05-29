```
chemicalelements(chemical::AbstractChemical; kwargs...)
```

`chemical`の要素を取得します。これは`getchemicalattr(chemical, :elements; kwargs...)`と同等ですが、要素が利用できない場合は`Pair{String, Int}[]`を返します。
