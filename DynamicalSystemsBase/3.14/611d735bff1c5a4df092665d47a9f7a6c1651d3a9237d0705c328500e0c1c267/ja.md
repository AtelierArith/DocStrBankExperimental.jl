```
successful_step(ds::DynamicalSystem) -> true/false
```

最後の `step!` 呼び出しが `ds` に対して成功した場合は `true` を返し、そうでない場合は `false` を返します。連続時間システムの場合、これは DifferentialEquations.jl のエラーチェックを使用し、離散時間の場合は任意の変数が `Inf` または `NaN` であるかどうかをチェックします。
