```
estimate_x0(sys, d, n = min(length(d), 3 * slowest_time_constant(sys)); fixed = fill(NaN, sys.nx)
```

システムの初期状態を推定します

# 引数:

  * `d`: [`iddata`](@ref)
  * `n`: 使用するサンプルの数。
  * `fixed`: `x0`と同じ長さのベクトルが提供される場合、有限値は推定されない固定値を示し、非有限値は自由です。

# 例

```julia
sys   = ssrand(2,3,4, Ts=1)
x0    = randn(sys.nx)
u     = randn(sys.nu, 100)
y,t,x = lsim(sys, u; x0)
d     = iddata(y, u, 1)
x0h   = estimate_x0(sys, d, 8, fixed=[Inf, x0[2], Inf, Inf])
x0h[2] == x0[2] # 正確な等式であるべき
norm(x0-x0h)    # 小さいはず
```
