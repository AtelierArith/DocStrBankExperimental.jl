```
metasymbols(md::MatrixDescriptor)
```

問題のメタデータを指すシンボルのベクトルを返します。これらのシンボル `s` は `getproperty(md, s)` または `getindex(md, s)` によってオブジェクトにアクセスするために使用できます。定数 `Julia` 単語である場合は、構文 `md.S` が推奨されます。いずれにせよ `md[s]` も可能です。

例: `md = mdopen("*/bfly"); A = md.A; co = md.coord; txt10 = md["Gname_10.txt"]`
