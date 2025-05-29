```
calculate_time_shared_production(ECModel::AbstractEC; kwargs...)
```

エネルギーコミュニティのための共有消費エネルギーの時系列を計算します。

各時間ステップとユーザーに対して、この時系列は他のユーザーによって満たされる生産量を強調します。

''' 出力 –––- shared*prod*us : DenseAxisArray     各ユーザーの共有生産と集計および時間ステップ '''
