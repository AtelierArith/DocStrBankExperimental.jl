```
hm(time_string::Union{AbstractString, Missing})::Time
```

"HH:MM" 形式の時間文字列を Time オブジェクトに変換します。

# 引数

`time_string`: 時間表現を含む文字列。

# 戻り値

入力文字列から解析された時と分の値を使用して構築された Time オブジェクト。すべてが正常に解析できた場合に返されます。入力が欠損している場合や、文字列から時間情報を解析できない場合は、欠損値を返します。

# 例

```jldoctest
julia> hm("09:30")
09:30:00

julia> hm("12:60")
missing
```
