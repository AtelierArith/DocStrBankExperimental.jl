```
pattern(str::AbstractString) -> Pattern
```

`j"str"` マクロの関数バージョン。ドキュメントについては [`@j_str`](@ref) を参照してください。

# 例

```jldoctest
julia> using CodeSearch: pattern

julia> pattern("a + (b + *)")
j"a + (b + *)"

julia> match(pattern("(b + *)"), "(b + 6)")
CodeSearch.Match((call-i b + 6), captures=[6])

julia> findall(pattern("* + *"), "(a+b)+(d+e)")
3-element Vector{UnitRange{Int64}}:
 1:11
 2:4
 8:10

julia> match(pattern("(* + *) \\* *"), "(a-b)*(d+e)") # マッチしない -> 何も返さない

julia> occursin(pattern("(* + *) \\* *"), "(a-b)*(d+e)")
false

julia> eachmatch(pattern("*(\"hello world\")"), "print(\"hello world\"), display(\"hello world\")")
2-element Vector{CodeSearch.Match}:
 Match((call print (string "hello world")), captures=[print])
 Match((call display (string "hello world")), captures=[display])

julia> count(pattern("*(*)"), "a(b(c))")
2

julia> match(pattern("(* + *) \\* *"), "(a+b)*(d+e)")
CodeSearch.Match((call-i (call-i a + b) * (call-i d + e)), captures=[a, b, (call-i d + e)])
```
