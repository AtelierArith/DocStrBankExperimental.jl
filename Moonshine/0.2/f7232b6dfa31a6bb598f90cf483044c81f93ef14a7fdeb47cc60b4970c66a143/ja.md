```
cbasis!(vec, arg, v, lk; estack, edgesid, vqueue, visited)
cbasis(arg, v, lk; estack, edgesid, vqueue, visited)
cbasis!(mat, arg; edgesid)
cbasis(arg; edgesid)
```

再結合頂点 `v` に関連付けられた基底ベクトルを計算します。`v` が指定されていない場合は、すべての基底ベクトルを含む行列を返します。
