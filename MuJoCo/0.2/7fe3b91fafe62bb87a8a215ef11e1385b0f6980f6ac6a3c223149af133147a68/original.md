```
mjd_transitionFD(m, d, eps, flg_centered, A, B, C, D)
```

Finite differenced transition matrices (control theory notation)   d(x_next) = A*dx + B*du   d(sensor) = C*dx + D*du   required output matrix dimensions:      A: (2*nv+na x 2*nv+na)      B: (2*nv+na x nu)      D: (nsensordata x 2*nv+na)      C: (nsensordata x nu)

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`eps::Float64`**
  * **`flg_centered::UInt8`**
  * **`A::Matrix{Float64}`** -> An **optional** matrix of variable size. `A` should be of shape (2*nv+na, 2*nv+na). Can set to `nothing` if not required.
  * **`B::Matrix{Float64}`** -> An **optional** matrix of variable size. `B` should be of shape (2*nv+na, nu). Can set to `nothing` if not required.
  * **`C::Matrix{Float64}`** -> An **optional** matrix of variable size. `C` should be of shape (nsensordata, 2*nv+na). Can set to `nothing` if not required.
  * **`D::Matrix{Float64}`** -> An **optional** matrix of variable size. `D` should be of shape (nsensordata, nu). Can set to `nothing` if not required.
