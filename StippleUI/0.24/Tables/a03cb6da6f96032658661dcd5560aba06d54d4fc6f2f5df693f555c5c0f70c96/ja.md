```
rowselection(dt::DataTable, rows, cols = Colon(), idcolumn = dt.opts.addid ? dt.opts.idcolumn : "__id")
```

行番号に基づいてテーブル選択を構築します。

Quasarの標準的な動作は、選択にすべての列を含めることです。

大きなテーブルでは、選択値の他の使用がない場合、インデックスのみを含めることが十分な場合があります。これは、`cols`を`nothing`に設定することで実現されます。

```
rowselection(dt, 3)
rowselection(dt, 2:5)
rowselection(dt, [2, 4, 7])
rowselection(dt, :, nothing)
```
