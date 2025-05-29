```
make_ito_process_syncronous_time_series(ito_processes::Union{Dict{Symbol,ItoProcess{T}},Dict{Symbol,ItoProcess}},
                                                 covar::Union{ForwardCovariance,SimpleCovariance}, timegap::R, total_number_of_ticks::Integer;
                                                 number_generator::NumberGenerator = Mersenne(MersenneTwister(2), length(collect(keys(ito_processes))))) where R<:Real where T<:Real
```

`ItoProcess`を前方に進化させます。

### 入力

  * `itoprocesses` - `ItoProcess`の`Dict`
  * `covar` - 共分散行列。
  * `timegap` - ティック間の時間ギャップ。
  * `total_number_of_ticks` - ティックの総数。
  * `number_generator` - RNGに使用される`NumberGenerator`。

### 戻り値

  * ティックを含むDataFrame。
