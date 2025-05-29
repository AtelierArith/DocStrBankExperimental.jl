```
rowselection(dt::DataTable, rows, cols = Colon(), idcolumn = dt.opts.addid ? dt.opts.idcolumn : "__id")
```

Build a table selection based on row numbers.

Standard behavior of Quasar is to include all columns in the selection.

For large tables it might be sufficient to include only the index, when no other use of the selection value is made. This is achieved by setting `cols` to `nothing`

```
rowselection(dt, 3)
rowselection(dt, 2:5)
rowselection(dt, [2, 4, 7])
rowselection(dt, :, nothing)
```
