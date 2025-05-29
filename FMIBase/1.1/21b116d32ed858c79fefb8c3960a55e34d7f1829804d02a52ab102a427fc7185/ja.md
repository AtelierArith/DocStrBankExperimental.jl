```
getTime(solution::FMUSolution)
```

ソリューションの時間を返します。

# 引数

  * `solution::FMUSolution`: 特定のFMUのソリューション `value`、`success`、`state` および `events` に関する情報を含む構造体です。

# 戻り値

  * `solution.states.t::tType`: `solution.state` は属性 t を持つ構造体 `ODESolution` です。`t` はODEソリューションの保存された値に対応する時間点です。
  * `solution.values.t::tType`: `solution.value` は属性 t を持つ構造体 `ODESolution` です。`t` はODEソリューションの保存された値に対応する時間点です。
  * ソリューション時間が見つからない場合は `nothing` が返されます。

#出典

  * using OrdinaryDiffEq: [ODESolution](https://github.com/SciML/SciMLBase.jl/blob/b10025c579bcdecb94b659aa3723fdd023096197/src/solutions/ode_solutions.jl)  (SciML/SciMLBase.jl)
  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.22]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
