```
hms(time_string::Union{String, Missing})
```

"HH:MM:SS" 形式の時間文字列を Time オブジェクトに変換します。入力文字列がこの形式に一致しない場合や変換できない場合は、エラーがスローされます。

# 引数

`time_string`: 時間を表す文字列または欠損値。文字列は "HH:MM:SS" 形式である必要があります。入力時間文字列を表す Time オブジェクトを返します。

# 例

```jldoctest
julia> hms("12:34:56")
12:34:56

julia> hms(missing)
missing
```
