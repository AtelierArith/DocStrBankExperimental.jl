```
ising2d!(s=rand_ising2d(), β=β_ising2d, niters=10^3, rng=default_rng();
    algorithm=default_algorithm())
```

は、2次元イジングモデルのルールに従って、±1の値で2次元配列`s`をランダムに更新します。

例1:

```julia
using Ising2D
@time s = ising2d!(rand_ising2d(), β_ising2d, 10^5)
plot_ising2d(s)
```

例2:

```julia
using Ising2D
@time s = ising2d!(rand_ising2d(), β_ising2d, 10^5; algorithm=IfElse())
plot_ising2d(s)
```
