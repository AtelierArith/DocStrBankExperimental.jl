```
poly(pointlist::Vector{Point}, action = :none;
    close=false,
    reversepath=false)
```

ポリゴンを描画します。`pointlist`内のポイントを使用してパスを作成し、`action`を適用します。デフォルトでは、`poly()`はポリゴンを閉じたり塗りつぶしたりしません。
