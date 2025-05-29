```
rc_f(;rho_x::T, eps_x::T, c_x::T, rho_m::T, eps_m::T, c_m::T, rho_g::T, eps_g::T, c_g::T)::T where {T<:Float64}
```

密度と比熱の積を計算する

  * この関数は `build_rho_rc` 関数内で使用されます。

## 戻り値

  * `rc`: 密度と比熱の積
