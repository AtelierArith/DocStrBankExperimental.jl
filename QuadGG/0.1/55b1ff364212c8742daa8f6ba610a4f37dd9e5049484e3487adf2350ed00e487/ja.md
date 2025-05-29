```
adaptlob(f,a,b; tol::Real=1e-10, trace::Bool=false)
```

閉区間 `[a,b]` にわたって `f` を許容誤差 `tol` 以内で数値的に積分します。これは Gander と Gautschi (2000) による適応ガウス・ロバット法を使用しています。

`trace=true` を渡すと、関数がサンプリングされている場所に関する情報が出力されます。

`f` は `a` と `b` で定義されている必要があります。

```
using QuadGG
adaptlob(sqrt,0,1)
```
