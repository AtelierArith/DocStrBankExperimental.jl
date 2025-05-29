```
inner(M::Tucker, p::TuckerPoint, X::TuckerTangentVector, Y::TuckerTangentVector)
```

タッカーマンフォールドの点 `p` における接ベクトル `X` と `Y` の間のユークリッド内積。これは `embed(M, p, X) ⋅ embed(M, p, Y)` に等しいです。

```
inner(::Tucker, A::TuckerPoint, X::TuckerTangentVector, Y)
inner(::Tucker, A::TuckerPoint, X, Y::TuckerTangentVector)
```

接ベクトル `X` が `p` におけるタッカーマンフォールドに接しているベクトルであり、`Y` が周囲の空間のベクトル、またはその逆である場合の `X` と `Y` の間のユークリッド内積。周囲の空間のベクトルはフルテンソル、すなわち多次元配列として表されます。
