```
untokenise!(txt::Txt, W::Union{AbstractCharSpace, Nothing} = nothing; kwargs)
```

`txt`をその場でアン・トークン化し、`raw::String`フィールドと`is_tokenised`を更新し、`tokenised`をクリアします。

# 例

```julia-repl
julia> t
12-token Txt:
[13, 18, 23, 15, 15, 4, 13, 15, 13, 5, 14, 20]

julia> untokenise!(t)
14-character Txt:
"Mr Wood moment"
```
