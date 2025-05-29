この関数は回帰問題のための線形システムを設定するために使用されます。行列 A とベクトル b を返し、A*x = b となります。ここで、x はパラメータのベクトルです。

```
setup_linear_system(sys::AbstractTimeDependentSystem)
```

# 引数

  * `sys`: パラメータのために解決される方程式のシステム (ODESystem または DAESystem)

# 戻り値

  * `A`: 方程式 A*x = b における記号的行列 A
  * `b`: 方程式 A*x = b における記号的ベクトル b
