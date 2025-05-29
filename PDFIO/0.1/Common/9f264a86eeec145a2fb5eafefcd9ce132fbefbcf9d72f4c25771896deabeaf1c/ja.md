```
    CDDate(s::CDTextString)
```

PDFファイルは次の文字列形式をサポートしています: (D:YYYYMMDDHHmmSSOHH'mm)

# 例

```
julia> date = CDDate("D:20190425173659+05'30")
D:20190425173659+05'30

julia> date.d
2019-04-25T17:36:59

julia> date.tz
5時間30分

julia> date.ahead
true
```
