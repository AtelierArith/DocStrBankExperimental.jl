```
evolve(c::CurveProblem, solmethod=Tsit5; mdc_callback=nothing, callback=nothing, saved_values=nothing, momentum_tol=1e-3,kwargs...)
```

最小限の干渉を伴う曲線を進化させます。曲線のパラメータはcurveProblemによって指定されます。DifferentialEquations.solve()を使用してODEを実行します。MinimallyDisruptiveCurves.jlのコールバックは`mdc_callback`キーワード引数に入れます。また、DifferentialEquations.solve()と互換性のある任意のDifferentialEquations.jlのコールバックを使用することもできます。それらは`callback`キーワード引数に入れます。
