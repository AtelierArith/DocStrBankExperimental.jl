```
j"str" -> パターン
```

`Pattern`を構築します。例えば、`j"a + (b + *)"`のように、Juliaコードにマッチします。

`*`文字は任意の式にマッチするワイルドカードであり、マッチングは空白やコメントに関係なく行われます。`"`と`*`の文字だけがエスケープされる必要があり、補間はサポートされていません。

補間が必要な場合は、このマクロの関数バージョンについて[`pattern`](@ref)を参照してください。

# 例

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

julia> match(j"(* + *) \* *", "(a-b)*(d+e)") # マッチしない -> 何も返さない

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
