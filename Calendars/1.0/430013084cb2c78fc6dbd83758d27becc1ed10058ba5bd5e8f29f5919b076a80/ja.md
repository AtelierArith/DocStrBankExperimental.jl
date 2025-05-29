```julia
DayNumberFromDate(date::Cdate, string::Bool, show::Bool)
```

カレンダーの日付に対応する日番号を返します。日付の部分は別々に指定することもできます。

オプションのパラメータ `string` が `true` の場合、関数は日番号を文字列形式で返します。そうでない場合は整数として返します。`string` のデフォルトは 'false' です。

オプションのパラメータ `show` が 'true' の場合、日付と番号が印刷されます。`show` のデフォルトは 'false' です。

例えば：

```julia
julia> DayNumberFromDate("Gregorian", 1756, 1, 27) 
```

「共通紀元」を意味する略語 CE を使用すると、これは次のようにも書けます。

```julia
julia> DayNumberFromDate(CE, 1756, 1, 27) 
```

これにより、デフォルトで整数としてヨーロッパの日番号 641027 が返されます。`string` が `true` の場合、文字列 "EN#641029" が返されます。`show` が `true` の場合、行 "CE-1756-01-27 -> EN#641029" が印刷されます。

エラーが発生した場合は、0（無効な日番号を表す）が返されます。
