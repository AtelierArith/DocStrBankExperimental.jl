```
chemicalformula(chemical::AbstractChemical; kwargs...)
```

`chemical`の式を取得します。これは`getchemicalattr(chemical, :formula; kwargs...)`と同等ですが、式が利用できない場合は`""`を返します。
