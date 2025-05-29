```
gcd(p1::StandardBasisPolynomial, p2::StandardBasisPolynomial; method=:euclidean, kwargs...)
```

最大公約数を求めます。

デフォルトでは、ユークリッド除法アルゴリズム（`method=:euclidean`）を使用しますが、これは浮動小数点の問題に影響を受けやすいです。

`method=:noda_sasaki`を渡すと、これらのいくつかを回避するためにスケーリングが使用されます。

`method=:numerical`を渡すと、数値的なgcdのために内部メソッド`NGCD.ngcd`が呼び出されます。詳細については`NGCD.ngcd`のドキュメントを参照してください。
