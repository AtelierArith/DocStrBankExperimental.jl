Ising2D is a simple Julia module of 2D Ising model.

Benchmark 1:

```julia
using Ising2D, BenchmarkTools
s = rand_ising2d()
print("VERSION = $VERSION:")
@btime ising2d!($s; algorithm=IfElse());
```

Benchmark 2:

```julia
using Ising2D, BenchmarkTools
s = rand_ising2d()
print("VERSION = $VERSION:")
@btime ising2d!($s; algorithm=MultiFor());
```
