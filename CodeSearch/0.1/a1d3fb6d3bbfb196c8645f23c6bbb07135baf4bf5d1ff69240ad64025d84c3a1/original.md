```
j"str" -> Pattern
```

Construct a `Pattern`, such as `j"a + (b + *)"` that matches Julia code.

The `*` character is a wildcard that matches any expression, and matching is performed insensitive of whitespace and comments. Only the characters `"` and `*` must be escaped, and interpolation is not supported.

See [`pattern`](@ref) for the function version of this macro if you need interpolation.

# Examples

```jldoctest
julia> j"a + (b + *)"
j"a + (b + *)"

julia> match(j"(b + *)", "(b + 6)")
CodeSearch.Match((call-i b + 6), captures=[6])

julia> findall(j"* + *", "(a+b)+(d+e)")
3-element Vector{UnitRange{Int64}}:
 1:11
 2:4
 8:10

julia> match(j"(* + *) \* *", "(a-b)*(d+e)") # no match -> returns nothing

julia> occursin(j"(* + *) \* *", "(a-b)*(d+e)")
false

julia> eachmatch(j"*(\"hello world\")", "print(\"hello world\"), display(\"hello world\")")
2-element Vector{CodeSearch.Match}:
 Match((call print (string "hello world")), captures=[print])
 Match((call display (string "hello world")), captures=[display])

julia> count(j"*(*)", "a(b(c))")
2

julia> match(j"(* + *) \* *", "(a+b)*(d+e)")
CodeSearch.Match((call-i (call-i a + b) * (call-i d + e)), captures=[a, b, (call-i d + e)])
```
