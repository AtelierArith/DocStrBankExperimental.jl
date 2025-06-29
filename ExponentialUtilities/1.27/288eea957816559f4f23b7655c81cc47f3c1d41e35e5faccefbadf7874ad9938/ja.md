```
KrylovSubspace{T}(n,[maxiter=30]) -> Ks
KrylovSubspace{T, U, VType}(n,[maxiter=30]) -> Ks
```

初期化されていないクライロフ部分空間を構築し、`arnoldi!`によって埋めることができます。

部分空間の次元 `Ks.m` は動的に変更できますが、最大許容アーノルディ反復である `maxiter` より小さい必要があります。

(拡張された) 正規直交基底ベクトル行列 `V` の型は `VType` として指定できます。これは、例えば `GPUArray` に必要です。

`U` は `eltype(H)` を決定します。

```
getV(Ks) -> V
getH(Ks) -> H
```

(拡張された) 正規直交基底 `V` と (拡張された) グラム・シュミット係数 `H` へのアクセスメソッド。両方のメソッドはストレージ配列へのビューを返し、`Ks.m` に示される正しい次元を持っています。

```
resize!(Ks, maxiter) -> Ks
```

`Ks` を異なる `maxiter` にリサイズし、その内容を破壊します。

これは高コストの操作であり、稀に使用するべきです。
