```
adaptsim(f,a,b; tol::Real=1e-10, trace::Bool=false)
```

閉区間 `[a,b]` で関数 `f` を許容誤差 `tol` まで数値的に積分します。これは Gander と Gautschi (2000) の適応シンプソン法を使用しています。

`trace=true` を渡すと、関数がサンプリングされている場所に関する情報が出力されます。

`f` は `a` と `b` で定義されている必要があります。

```
using QuadGG
adaptsim(sqrt,0,1)
```
