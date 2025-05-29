```
format_angle(parts; delim=':')
```

与えられた角度の `(whole, minutes, seconds)` 部分を、指定された区切り文字で文字列にフォーマットします。これらの部分は、性分数および `hour:minute:second` 出力のための `xxx2dms` および `xxx2hms` メソッドによって生成できます。複数の区切り文字は、それぞれの値の後に配置されたタプルまたはベクターで指定できます。フォーマットに対するより細かな制御が必要な場合は、[Printf](https://docs.julialang.org/en/v1/stdlib/Printf/) や [Format.jl](https://github.com/JuliaString/Format.jl) のようなパッケージの使用を検討してください。

# 例

```jldoctest
julia> ang = 45.0; # 度

julia> format_angle(deg2dms(ang))
"45:0:0.0"

julia> format_angle(deg2hms(ang))
"3:0:0.0"

julia> format_angle(rad2hms(1.5), delim=["h", "m", "s"])
"5h43m46.48062470963538s"
```

# 参照

[`deg2dms`](@ref), [`deg2hms`](@ref), [`rad2dms`](@ref), [`rad2hms`](@ref), [`ha2dms`](@ref), [`ha2hms`](@ref)
