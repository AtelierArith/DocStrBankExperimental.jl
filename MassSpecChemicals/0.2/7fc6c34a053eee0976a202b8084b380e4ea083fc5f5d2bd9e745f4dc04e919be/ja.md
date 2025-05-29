```
rt(chemical::AbstractChemical; kwargs...)
```

`chemical`の保持時間を取得します。これは、`getchemicalattr(chemical, :rt; kwargs...)`と同等ですが、rtが利用できない場合は`NaN`を返します。
