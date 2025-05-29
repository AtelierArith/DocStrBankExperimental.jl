```
QuadratureFunction(; fun=trapz, npt=50, nthreads=1)
```

標準区間[-1,1]のための数値積分ルールは、関数`x, w = fun(npt)`から計算されます。ノードと重みは、[-1,1]上の`f`の積分が`sum(w .* f.(x))`になるように設定されるべきです。デフォルトの数値積分ルールは[`trapz`](@ref)ですが、他のパッケージもルールを提供しています。例えば、

```
using FastGaussQuadrature
alg = QuadratureFunction(fun=gausslegendre, npt=100)
```

`nthreads`は、被積分関数がある場合にのみ数値積分を並列化するために使用されるスレッドの数を設定します。この場合、ユーザーは被積分関数の評価を並列化する必要があります。スレッドを使用しない場合は`nthreads=1`に設定します。
