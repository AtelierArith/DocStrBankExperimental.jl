```julia
abstract type Curl2D <: ??
```

は、ある二次元ベクトル場のカールを評価します。すなわち、Curl2D((u1,u2)) = du2/dx1 - du1/dx2 です。
