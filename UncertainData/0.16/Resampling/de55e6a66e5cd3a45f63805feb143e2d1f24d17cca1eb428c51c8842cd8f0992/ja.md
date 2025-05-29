```
resample_elwise(uvd::UVAL_COLLECTION_TYPES, n::Int)
```

`uvals`の各要素を`n`回再サンプリングします。返されるベクトルのi番目のエントリは、`uvals[i]`の`n`個のユニークな引き出しからなる`n`要素のベクトルです。
