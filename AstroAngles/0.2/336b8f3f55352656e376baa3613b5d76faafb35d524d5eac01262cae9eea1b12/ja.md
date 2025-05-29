```
dms2ha(degrees, arcmin, arcsec)
dms2ha(parts)
dms2ha(input::AbstractString)
```

(degrees, arcminutes, arcseconds) のタプルを時間角に変換します。文字列が与えられた場合は、最初に [`parse_dms`](@ref) で解析します。角度が入力された場合は、何もしないものとして扱います。
