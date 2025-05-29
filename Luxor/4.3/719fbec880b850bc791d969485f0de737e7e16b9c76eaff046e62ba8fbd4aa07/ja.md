```
isinside(p::Point, pointlist::Vector{Point}
    allowonedge = false)
```

点 `p` は多角形 `pointlist` の内部にありますか？

`allowonedge` が false の場合、多角形上にある点は内部とは見なされません。

内部にある場合は true を返し、そうでない場合は false を返します。
