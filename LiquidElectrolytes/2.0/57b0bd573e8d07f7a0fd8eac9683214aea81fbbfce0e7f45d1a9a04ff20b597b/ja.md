```
function dlcapsweep(
        sys;
        electrolyte = electrolytedata(sys),
        inival = nothing,
        voltages = (-1:0.1:1) * ufac"V",
        δ = 1.0e-4,
        store_solutions = false,
        solver_kwargs...
    )
```

与えられた`voltages`の電圧に対する二重層キャパシタンスを計算します。 [`DLCapSweepResult`](@ref)を返します。

前提条件：

  * システム内に二重層は1つのみ - 作動電極に近い。
