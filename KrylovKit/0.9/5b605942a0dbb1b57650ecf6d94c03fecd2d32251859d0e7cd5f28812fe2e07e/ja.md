```
v = InnerProductVec(vec, dotf)
```

既存のベクトル `dotf` から修正された内積によって新しいベクトル `v` を作成します。ベクトル `vec` は、KrylovKit に必要な基本的なベクトルインターフェースをサポートする任意のタイプ（必ずしも `Vector` である必要はありません）であり、カスタム構造体 `v::InnerProductVec` にラップされています。加算やスカラーとの乗算（両方とも場所を変えずに、`mul!`、`rmul!`、`axpy!`、`axpby!` を使用して場所を変えて）などのすべてのベクトル空間機能は、単に `v.vec` に転送されます。ベクトル `v1 = InnerProductVec(vec1, dotf)` と `v2 = InnerProductVec(vec2, dotf)` の間の内積は、`dot(v1, v2) = dotf(v1.vec, v2.vec) = dotf(vec1, vec2)` として計算されます。異なる `dotf` 関数を持つベクトル間の内積は定義されていません。同様に、`v::InnerProductVec` のノルムは `v = sqrt(real(dot(v, v))) = sqrt(real(dotf(vec, vec)))` として定義されます。

`v` に適用された（線形）マップでは、元のベクトルは `v.vec` または単に `v[]` として取得できます。
