```
window(tns, dims)
```

別のテンソルへのビューを表す `WindowedArray` を作成します

```
    window(tns, dims)[i...] == tns[dim[1][i], dim[2][i], ...]
```

ウィンドウ配列は、新しい次元を各 `dim` の有効なインデックスの次元に制限します。 `dims` は、基になる次元の完全なビューを表すために `nothing` であることもできます。
