```
nsmallest(n, arr; kw...)
```

配列 `arr` の `n` 個の最小要素を返します。

等価:     sort(arr; kw...)[1:min(n, end)]

`arr` が浮動小数点数を含み、NaN 値が含まれていない場合、次の代替手段を使用して 2 倍のパフォーマンスを達成できます:

```
DataStructures.nextreme(DataStructures.FasterForward(), n, arr)
```

この高速バージョンは次のように等価です:

```
sort(arr, lt = <)[1:min(n, end)]
```
