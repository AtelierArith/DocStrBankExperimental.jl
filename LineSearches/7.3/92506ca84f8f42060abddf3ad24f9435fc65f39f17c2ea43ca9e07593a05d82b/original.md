`StrongWolfe`: This linesearch algorithm guarantees that the step length satisfies the (strong) Wolfe conditions. See Nocedal and Wright - Algorithms 3.5 and 3.6

This algorithm is mostly of theoretical interest, users should most likely use `MoreThuente`, `HagerZhang` or `BackTracking`.

## Parameters:  (and defaults)

  * `c_1 = 1e-4`: Armijo condition
  * `c_2 = 0.9` : second (strong) Wolfe condition
  * `ρ = 2.0` : bracket growth
