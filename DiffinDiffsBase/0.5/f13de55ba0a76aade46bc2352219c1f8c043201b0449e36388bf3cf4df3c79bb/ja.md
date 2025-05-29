```
subcolumns(data, names, rows=Colon(); nomissing=true)
```

[`VecColumnTable`](@ref)を`data`から、選択した`rows`に対して`names`で指定された列を使用して構築します。

デフォルトでは、列は欠損値のサポートを削除するように変換されます。可能な場合、結果の列は元の列とメモリを共有します。
