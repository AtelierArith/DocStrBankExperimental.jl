```
SparseFiniteGP{T1<:FiniteGP, T2<:FiniteGP}
```

`AbstractGP` `f` の有限次元射影で、位置 `x` で定義され、近似推論を行うために疎な誘導点のセット [1] で定義された第二の `FiniteGP` を使用します。

このオブジェクトは通常の `FiniteGP` と似たメソッドを持っていますが、`logpdf` を呼び出すと実際には `elbo` を計算し、`posterior` を呼び出すと近似後方分布を得ることができます。

[1] - M. K. Titsias. "Variational learning of inducing variables in sparse Gaussian processes". In: Proceedings of the Twelfth International Conference on Artificial Intelligence and Statistics. 2009.

```jldoctest
julia> f = atomic(GP(Matern32Kernel()), GPC());

julia> fobs = f(rand(100));

julia> finducing = f(0:0.1:1);

julia> fxu = SparseFiniteGP(fobs, finducing);

julia> y = rand(fxu);

julia> logpdf(fxu, y) < logpdf(fobs, y)
true
```
