実際の2つの日付の間の日数

```
	ndays=daysact(Date1,Date2)
```

ここで：

```
	Date1 = 開始日。
	Date2 = 終了日。

	ndays      = 開始日と終了日の間の日数。
```

# 例

```julia-repl
julia> daysact(Date(1996,10,12),Date(1998,1,10))
455
```
