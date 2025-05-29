```
nlargest(n, arr; kw...)
```

配列 `arr` の `n` 個の最大要素を返します。

等価なもの:     sort(arr, kw..., rev=true)[1:min(n, end)]

`arr` に浮動小数点数が含まれていて、NaN 値が含まれていない場合、次の代替手段を使用して 2 倍のパフォーマンスを達成できます:

```
DataStructures.nextreme(DataStructures.FasterReverse(), n, arr)
```

この高速バージョンは次のように等価です:

```
sort(arr, lt = >)[1:min(n, end)]
```
