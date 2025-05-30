```
IMEXEuler(;kwargs...)
```

IMEX多段法の1ステップバージョン

  * Uri M. Ascher, Steven J. Ruuth, Brian T. R. Wetton. Implicit-Explicit Methods for Time-Dependent Partial Differential Equations. Society for Industrial and Applied Mathematics. Journal on Numerical Analysis, 32(3), pp 797-823, 1995. doi: [https://doi.org/10.1137/0732037](https://doi.org/10.1137/0732037)

`SplitODEProblem`の形式に適用されると

```
u'(t) = f1(u) + f2(u)
```

デフォルトの`IMEXEuler()`メソッドは、次の形式の更新を使用します

```
unew = uold + dt * (f1(unew) + f2(uold))
```

`SBDF`、`IMEXEulerARK`も参照してください。
