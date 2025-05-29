```julia
DatePicker(; [default::Dates.Date])
```

日付入力 - ユーザーは日付を選択でき、選択された日付は `Dates.Date` として返されます。

`default` キーワード引数を使用して初期値を設定します。初期値が指定されていない場合、バウンド値は日付が選択されるまで `nothing` に設定されます。

# 例

```julia
@bind date1 DatePicker()
```

```julia
using Dates

@bind date2 DatePicker(default=Date(2022, 12, 14))
```
