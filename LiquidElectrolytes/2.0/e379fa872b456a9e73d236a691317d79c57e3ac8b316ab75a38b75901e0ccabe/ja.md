```
 ivsweep(
      sys;
      voltages = (-0.5:0.1:0.5) * ufac"V",
      store_solutions = false,
      solver_kwargs...,
      )
```

定常状態ボルタンメトリー。

`voltages`の各電圧に対するモル反応速度とバルクフラックス速度を計算します。[`IVSweepResult`](@ref)を返します。
