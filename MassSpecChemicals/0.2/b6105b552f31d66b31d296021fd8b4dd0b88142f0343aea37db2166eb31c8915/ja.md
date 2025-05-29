```
chemicalsmiles(chemical::AbstractChemical; kwargs...)
```

`chemical`のSMILESを取得します。これは`getchemicalattr(chemical, :SMILES; kwargs...)`と同等ですが、SMILESが利用できない場合は`""`を返します。
