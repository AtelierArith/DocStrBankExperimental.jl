```julia
CalendarDates(date::CDate, show::Bool)
```

指定された `date` に対応するすべてのサポートされているカレンダーの日付のテーブルを返します。オプションのパラメータ `show` が 'true' に設定されている場合、日付テーブルが印刷されます。`show` はデフォルトで 'false' です。

```julia
julia> CalendarDates("Gregorian", 1756, 1, 27, true) 
```

また、次のように書くこともできます。

```julia
julia> CalendarDates(CE, 1756, 1, 27, true) 
```

これは `DateTable` を計算します。`DateTable` は6つのカレンダー日付とユーロ日数、ユリウス日数のタプルです。`show` が 'true' の場合、以下のテーブルが印刷されます。

```julia
    European  EC-1756-01-27
    Common    CE-1756-01-27
    Julian    JD-1756-01-16
    Hebrew    AM-5516-11-25
    Islamic   AH-1169-04-24
    IsoDate   ID-1756-05-02
    EuroNum   EN#0641029
    JulianNum JN#2362452
```
