```
solve_NR(f, f_prime, errorTol::T, count_max::T, Xc_initial::T)::T where {T<:Float64}
```

  * ガス中のCO2のモル分率 (X_CO2) を求める。
  * この関数は `exsolve3` 関数内で使用されます。

## 引数

  * `f`: 水の分配関数
  * `f_prime`: X_CO2 に関する水の導関数
  * `errorTol`: 誤差許容値、デフォルト値は 1e-10
  * `count_max`: 最大ループ回数、デフォルト値は 1e2
  * `Xc_initial`: X_CO2 の初期推定値、デフォルト値は 1e-2

## 戻り値

  * `X_CO2`: ガス中のCO2のモル分率
