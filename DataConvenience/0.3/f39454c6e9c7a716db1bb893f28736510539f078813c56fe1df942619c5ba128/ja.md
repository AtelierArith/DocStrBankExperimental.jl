```
onehot(df, col, cate = sort(unique(df[!, col])); outnames = Symbol.(:ohe_, cate))

onehot!(df, col, cate = sort(unique(df[!, col])); outnames = Symbol.(:ohe_, cate))
```

列をワンホットエンコードし、列を作成します。出力列は警告なしに上書きされます。

引数:

```
df   -   DataFrame
col  -   ワンホットエンコードする列
cate -  カテゴリ
```
