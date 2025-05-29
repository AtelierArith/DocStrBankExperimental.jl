```julia
SavingCallback(save_func, saved_values::SavedValues;
    saveat = Vector{eltype(saved_values.t)}(),
    save_everystep = isempty(saveat),
    save_start = true,
    tdir = 1)
```

保存コールバックを使用すると、保存する量を返す関数 `save_func(u, t, integrator)` を定義できます。

## 引数

  * `save_func(u, t, integrator)` は保存する量を返します。出力は `u` へのビューではなく、出力を割り当てる必要があります。
  * `saved_values::SavedValues` は `save_func` が返す型です。すなわち、`save_func(t, u, integrator)::savevalType` です。これは `SavedValues(typeof(t),savevalType)` を介して指定されます。すなわち、時間の型と `save_func` が出力する型（またはそれに互換性のある型）を指定します。

## キーワード引数

  * `saveat` は `solve` の `saveat` を模倣します。
  * `save_everystep` は `solve` の `save_everystep` を模倣します。
  * `save_start` は `solve` の `save_start` を模倣します。
  * `save_end` は `solve` の `save_end` を模倣します。
  * `tdir` は `sign(tspan[end]-tspan[1])` であるべきです。デフォルトは `1` で、`tspan[1] > tspan[end]` の場合は適応する必要があります。

出力された値は `saved_values` に保存されます。時間点は `saved_values.t` を介して見つけられ、値は `saved_values.saveval` です。
