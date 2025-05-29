```
Integrate1D(F::Function, Cube::HyperCube; tol::Real=1e-14, FullSol::Bool=false, meth=Tsit5())
```

`F`を`HyperCube`で指定された1次元領域にわたって積分します。これは、積分をODEとして言い換え、`DifferentialEquations.jl`を使用します。
