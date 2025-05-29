```
strictmap!(f, dst, src) -> dst
strictmap!(dst, f, src) -> dst
```

は、すべてのインデックス `i` に対して `dst[i] = f(src[i])` を実行し、`dst` を返します。引数 `dst` と `src` は同じ軸を持っている必要があります。

軸に関する厳密な条件を除けば、このメソッドは `map!(f,dst,src)` に似ています。
