```
ALFcompute(expiβ, nmax)
ALFcompute!(P̄, expiβ, nmax)
ALFcompute(expiβ, nmax, recursion_coefficients)
ALFcompute!(P̄, expiβ, nmax, recursion_coefficients)
```

最大 `n` 値 `nmax` までの「完全に正規化された」関連レジェンド関数を計算します。

これらの関数は、データを格納するためのベクトル P̄ を受け取ることができ、最も急速に変化する `m` の増加順に、次に `n` の増加順に格納されます。 提供されない場合、P̄ は自動的に構築され、返されます。

オプションの `recursion_coefficients` 引数は `ALFRecursionCoefficients` でなければならず、再帰に使用されるさまざまな定数係数を格納します。このオブジェクトは、この引数なしで単一の P̄ ベクトルを計算するのに 3 倍以上のメモリと 20 倍以上の時間を必要としますが、これを渡すことで通常は各 P̄ の計算を約 8 倍の速度で高速化します。したがって、P̄ を数回以上計算することが予想される場合は、これらの係数を事前に計算して、この関数に渡す方が時間が短縮されます。

基本の実数型は、`expiβ` の（複素）型から推測されます。存在する場合、P̄ と `recursion_coefficients` の基本型は一致している必要があります。
