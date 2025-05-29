```julia
DateFromDayNumber(calendar::DPart, enum::DPart, string::Bool, show::Bool)
```

カレンダーで表現されたヨーロッパの日数から日付を返します。

日数 `enum` は整数で、1以上でなければなりません。

オプションのパラメータ `string` が `true` の場合、関数は日付を文字列として返します。そうでない場合は整数のタプルとして返します。デフォルトでは `string` は `false` です。

オプションのパラメータ `show` が `true` に設定されている場合、日付と番号が印刷されます。デフォルトでは `show` は `false` です。

例えば：

```julia
julia> DateFromDayNumber("Gregorian", 641029) 
```

または次のように書くこともできます。

```julia
julia> DateFromDayNumber(CE, 641029) 
```

デフォルトでは、カレンダー表現 (2, 1756, 1, 27) が返されます。 `string` が `true` の場合、文字列 "CE-1756-01-27" が返されます。 `show` が 'true' の場合、行 "EN#0641029 -> CE-1756-01-27" が印刷されます。

エラーが発生した場合、(0, 0, 0, 0)（無効な日付を表す）が返されます。
