```
make_ito_process_non_syncronous_time_series(ito_processes::Union{Dict{Symbol,ItoProcess{R}},Dict{Symbol,ItoProcess}},
                                                 covar::Union{ForwardCovariance,SimpleCovariance}, update_rates::Union{OrderedDict{Symbol,D},Dict{Symbol,D},OrderedDict{Symbol,Distribution},Dict{Symbol,Distribution}},
                                                 total_number_of_ticks::Integer;
                                                 timing_twister::Union{StableRNG,MersenneTwister} = MersenneTwister(1),
                                                 ito_number_generator::NumberGenerator = Mersenne(MersenneTwister(2), length(collect(keys(ito_processes))))
                                                 ) where R<:Real where D<:Distribution
```

`ItoProcess`を前方に進化させます。

### 入力

  * `itoprocesses` - `ItoProcess`の`Dict`
  * `covar` - 共分散行列。
  * `update_rates` - 各資産のティック間の指数待機時間の更新率。
  * `total_number_of_ticks` - ティックの総数。
  * `ito_twister` RNGに使用される`MersenneTwister`。

### 戻り値

  * ティックを含むDataFrame。
