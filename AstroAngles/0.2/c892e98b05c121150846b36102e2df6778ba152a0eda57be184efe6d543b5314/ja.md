```
hms2ha(hours, mins, secs)
hms2ha(parts)
hms2ha(input::AbstractString)
```

(hours, 分, 秒) のタプルを時間角に変換します。文字列が与えられた場合は、最初に [`parse_hms`](@ref) で解析します。角度が入力された場合は、何もしないものとして扱います。
