```
 cvsweep(
      sys;
      voltages=SawTooth(),
      periods=1,
      solver_kwargs...,
      )
```

サイクリックボルタンメトリースイープ。デフォルトでは、`voltages`は[`SawTooth`](@ref)関数として与えられます。

モル反応速度と作業電極フラックス速度を計算します。[`CVSweepResult`](@ref)を返します。
