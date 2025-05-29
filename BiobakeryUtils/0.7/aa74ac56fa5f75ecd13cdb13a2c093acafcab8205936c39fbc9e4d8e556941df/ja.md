```
parsetaxa(taxstring::AbstractString; throw_error=true)
```

MetaPhlAnによってフォーマットされた分類群のランクを表す文字列（例："k**Bacteria|p**Proteobacteria..."）を与えると、分類群のランクをTaxon型の要素に分離し、ベクターに格納します。
