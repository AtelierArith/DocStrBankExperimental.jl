```
swizzle(tns, dims)
```

任意のテンソル `tns` を転置するために `SwizzleArray` を作成します。次のようになります。

```
    swizzle(tns, dims)[i...] == tns[i[dims]]
```
