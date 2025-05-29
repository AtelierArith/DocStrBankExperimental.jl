```
polysortbyangle(pointlist::Vector{Point}, refpoint=minimum(pointlist))
```

ポリゴンの点を順序に並べます。点は、指定された点との角度に従ってソートされます。

`refpoint` は選択できますが、デフォルトの最小点も通常は問題ありません：

```
polysortbyangle(parray, polycentroid(parray))
```
