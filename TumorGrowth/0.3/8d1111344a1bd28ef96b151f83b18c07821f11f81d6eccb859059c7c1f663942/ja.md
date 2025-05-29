```
bertalanffy_numerical(times, p; solve_kwargs...)
```

*テスト目的で提供されています。*

指定された `times` に対して、病変成長の一般的なバートランフィモデルの数値解に基づいて体積を返します。ここで `p` は `v0`、`v∞`、`ω`、`λ` のプロパティを持ち、`v0` は時間 `times[1]` における体積です。`solve_kwargs` は、DifferentialEquations.jl の ODE ソルバー `DifferentialEquations.solve` のためのオプションのキーワード引数です。

解析解に基づいているため、[`bertalanffy`](@ref) はこの関数の推奨される代替手段です。

!!! 重要     `times` が順序付けられていると仮定されており、チェックは行われません：`times == sort(times)`。

他にも [`bertalanffy2`](@ref) を参照してください。
