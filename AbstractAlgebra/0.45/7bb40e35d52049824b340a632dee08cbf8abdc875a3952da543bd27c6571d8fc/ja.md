```
similar(x::MatRingElem, R::NCRing, n::Int)
similar(x::MatRingElem, R::NCRing)
similar(x::MatRingElem, n::Int)
similar(x::MatRingElem)
```

与えられた環と次元に対して初期化されていない行列環要素を作成し、与えられたソース行列環要素 `x` に基づいてデフォルトを設定します。
