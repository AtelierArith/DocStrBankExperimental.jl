```
dms2rad(degrees, arcmin, arcsec)
dms2rad(parts)
dms2rad(input::AbstractString)
```

(degrees, arcminutes, arcseconds) のタプルをラジアンに変換します。文字列が与えられた場合は、最初に [`parse_dms`](@ref) で解析します。角度が入力された場合は、何もしないものとして扱います。
