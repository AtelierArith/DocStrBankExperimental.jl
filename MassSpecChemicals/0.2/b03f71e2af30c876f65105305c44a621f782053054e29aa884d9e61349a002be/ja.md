```
chemicalabbr(chemical::AbstractChemical; kwargs...)
```

`chemical`の略称を取得します。これは、略称が利用できない場合に`chemicalname(chemical; kwargs...)`を返すことを除いて、`getchemicalattr(chemical, :abbreviation; kwargs...)`と同等です。
