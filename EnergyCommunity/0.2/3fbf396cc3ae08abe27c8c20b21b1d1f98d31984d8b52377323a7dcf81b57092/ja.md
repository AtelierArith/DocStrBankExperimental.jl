```
calculate_time_shared_production(::AbstractGroupANC, ECModel::AbstractEC; add_EC=true, kwargs...)
```

協同ケースのための共有生産エネルギーの時系列を計算します。協同ケースでは、自己生産だけでなく、ユーザー間で共有されるエネルギーがあります。

各時間ステップとユーザーに対して、この時系列は他のユーザーによって満たされる生産量を強調します。

''' 出力 –––- shared*prod*us : DenseAxisArray     各ユーザーの共有生産と集計および時間ステップ '''
