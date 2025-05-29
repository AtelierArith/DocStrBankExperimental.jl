Ising2Dは2DイジングモデルのシンプルなJuliaモジュールです。

ベンチマーク 1:

```julia
using Ising2D, BenchmarkTools
s = rand_ising2d()
print("VERSION = $VERSION:")
@btime ising2d!($s; algorithm=IfElse());
```

ベンチマーク 2:

```julia
using Ising2D, BenchmarkTools
s = rand_ising2d()
print("VERSION = $VERSION:")
@btime ising2d!($s; algorithm=MultiFor());
```
