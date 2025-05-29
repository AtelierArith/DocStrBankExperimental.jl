```
IMEXEuler(;kwargs...)
```

IMEX多段法の1ステップバージョン

  * Uri M. Ascher, Steven J. Ruuth, Brian T. R. Wetton. 時間依存部分微分方程式のための暗黙-明示法。産業応用数学会。数値解析に関するジャーナル、32(3)、pp 797-823、1995年。doi: [https://doi.org/10.1137/0732037](https://doi.org/10.1137/0732037)

次の形式の`SplitODEProblem`に適用されると

```
u'(t) = f1(u) + f2(u)
```

デフォルトの`IMEXEuler()`メソッドは、次の形式の更新を使用します

```
unew = uold + dt * (f1(unew) + f2(uold))
```

`SBDF`、`IMEXEulerARK`も参照してください。
