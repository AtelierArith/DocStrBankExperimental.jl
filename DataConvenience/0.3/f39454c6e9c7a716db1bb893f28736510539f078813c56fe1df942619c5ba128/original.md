```
onehot(df, col, cate = sort(unique(df[!, col])); outnames = Symbol.(:ohe_, cate))

onehot!(df, col, cate = sort(unique(df[!, col])); outnames = Symbol.(:ohe_, cate))
```

One-hot encode a column and create columns. The output columns will be overwritten WITHOUT warning

Arguments:

```
df   -   The DataFrame
col  -   The column to onehot encode
cate -  The categories
```
