```
Dv = groupby(D::GMTdataset, col)::Vector{GMTdataset}
```

選択された `col` のユニークな値によって GMTdataset を分割します。

`col` は、文字列またはシンボルとしての列名、または列番号であることができます。いずれにせよ、整数（通常はフロート（浮動小数点整数））または文字列列を指す必要があります。*すなわち、* GMTdataset の最後の列です。
