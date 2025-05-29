```
Tenor(x:: AbstractString)
```

文字列からTenorオブジェクトを作成するためのコンストラクタです。入力文字列は、整数としての乗数の後に単位（最後の文字）を続けて始まる必要があります。

例:

```
julia> Tenor.(("1D", "3W", "1M", "10y"))
(Tenor(TDays, 1), Tenor(TWeeks, 3), Tenor(TMonths, 1), Tenor(TYears, 10))
```
