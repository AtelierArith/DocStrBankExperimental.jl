```julia
TimePicker(; [default::Dates.TimeType], [show_seconds::Bool=false])
```

時間入力 - ユーザーは時間を選択でき、選択された時間は `Dates.Time` として返されます。

`default` キーワード引数を使用して初期値を設定します。初期値が指定されていない場合、選択されるまでの間、バウンド値は `nothing` に設定されます。

# 例

```julia
@bind time1 TimePicker()
```

```julia
import Dates
@bind time2 TimePicker(default=Dates.Time(23,59,44))
```
