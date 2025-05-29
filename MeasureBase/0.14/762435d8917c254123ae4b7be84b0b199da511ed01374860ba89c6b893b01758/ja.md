```
pushfwd(f, μ, volcorr = WithVolCorr())
```

`μ` からの [プッシュフォワード測度](https://en.wikipedia.org/wiki/Pushforward_measure) を返します。測度関数 `f` は [可測関数](https://en.wikipedia.org/wiki/Measurable_function) です。

逆関数を手動で指定するには、`pushfwd(InverseFunctions.setinverse(f, finv), μ, volcorr)` を呼び出します。
