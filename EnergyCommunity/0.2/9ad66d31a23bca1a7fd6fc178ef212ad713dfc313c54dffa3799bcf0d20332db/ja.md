```
calculate_time_shared_consumption(::AbstractGroupNC, ECModel::AbstractEC; add_EC=true, kwargs...)
```

協力ケースのための共有消費エネルギーの時系列を計算します。協力ケースでは、自己生産だけでなく、ユーザー間で共有されるエネルギーがあります。

各時間ステップとユーザーに対して、この時系列は共有エネルギーを使用して満たされる負荷の量を強調します。

''' 出力 –––- shared*cons*us : DenseAxisArray     各ユーザーの共有消費と集約および時間ステップ '''
