```
nvecs(X,n,r=0;flipsign=false,svds=false)
nvecs(X::ttensor,n,r=0;flipsign=false)
nvecs(X::ktensor,n,r=0;flipsign=false)
```

テンソル X のモード-n 行列化の r 個の主特異ベクトルを計算します。XₙXₙᵀ で動作します。

## 引数:

  * `flipsign=true`: 最大の絶対値の要素を正にします。
  * `svds=true`: Xₙ に対して eigs ではなく svds を使用します。
