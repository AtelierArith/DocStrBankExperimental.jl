```
Box{D,T}(first::SVector{D}, last::SVector{D})
Box(first::SVector{D}, last::SVector{D})
```

指定された下限と上限を持つボックス領域を作成します。境界はベクトルとして与えられ、その要素の（いくつかは）無限大である可能性があります。各次元で `first < last` の制約が成り立たなければなりません。
