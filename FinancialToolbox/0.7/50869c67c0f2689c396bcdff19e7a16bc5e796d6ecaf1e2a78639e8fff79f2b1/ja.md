年のフラクションを2つの日付の間で、次の規則に従って計算します。

```
	yfr=yearfrac(Date1,Date2,basis)
```

ここで：

```
	Date1 = 開始日。
	Date2 = 終了日。
	basis = 次の規則を表す整数：
			- 0 = (ACT/ACT)
			- 1 = (30/360 SIA)
			- 2 = (ACT/360)
			- 3 = (ACT/365)
			- 4 = (30/360 PSA)
			- 5 = (30/360 ISDA)
			- 6 = (30E/360)
			- 7 = (ACT/365 JPN)

	yfr      = 開始日と終了日間の年のフラクション（basisに従う）。
```

# 例

```julia-repl
julia> yearfrac(Date(1996,10,12),Date(1998,1,10),1)
1.2444444444444445
```
