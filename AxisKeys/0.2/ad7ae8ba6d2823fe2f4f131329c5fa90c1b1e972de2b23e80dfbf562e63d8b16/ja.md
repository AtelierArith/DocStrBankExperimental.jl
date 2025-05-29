```
sortslices(A; dims)
sortkeys(A; dims=1:ndims(A))
```

`Base.sortslices` は、対応するキーも同じ次元に沿ってソートします。デフォルトのキーワード `by=vec` を使って、任意の形状のスライスで動作するように、概ね `p = sortperm(eachslice(A))` の実装を呼び出します。

`sortkeys(A)` は、キーによってすべてをソートします。デフォルトでは、任意の数の次元に沿って、すべての次元で動作します。
