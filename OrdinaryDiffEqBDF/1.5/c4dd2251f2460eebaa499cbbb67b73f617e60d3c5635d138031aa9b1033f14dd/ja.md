```
IMEXEulerARK(;kwargs...)
```

IMEX多段法の1ステップバージョン

  * Uri M. Ascher, Steven J. Ruuth, Brian T. R. Wetton. 時間依存部分微分方程式のための暗黙-明示法。産業応用数学会。数値解析に関するジャーナル, 32(3), pp 797-823, 1995. doi: [https://doi.org/10.1137/0732037](https://doi.org/10.1137/0732037)

次の形式の`SplitODEProblem`に適用されると

```
u'(t) = f1(u) + f2(u)
```

[Araújo, Murua, Sanz-Serna (1997)](https://doi.org/10.1137/S0036142995292128)の意味での古典的な加法的ルンゲ・クッタ法で、暗黙法と明示法のオイラー法から構成されます。

```
y1   = uold + dt * f1(y1)
unew = uold + dt * (f1(unew) + f2(y1))
```

`SBDF`、`IMEXEuler`も参照してください。
