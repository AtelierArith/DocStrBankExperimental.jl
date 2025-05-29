```
hms2deg(hours, mins, secs)
hms2deg(parts)
hms2deg(input::AbstractString)
```

（時間、分、秒）のタプルを度に変換します。文字列が与えられた場合は、最初に[`parse_hms`](@ref)で解析します。角度が入力された場合は、何もしないものとして扱います。
