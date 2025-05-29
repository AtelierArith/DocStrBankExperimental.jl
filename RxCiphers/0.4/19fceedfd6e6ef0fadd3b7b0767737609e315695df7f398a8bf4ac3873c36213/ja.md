```
tokenise!(txt::Txt, W::NCharSpace{1} = Alphabet)
```

`txt`をその場でトークン化し、`tokenised`、`frozen`、`is_tokenised`、`charspace`フィールドを更新します。

# 例

```julia-repl
julia> t = Txt("Mr Wood moment")
14-character Txt:
"Mr Wood moment"

julia> tokenise!(t)
12-token Txt:
[13, 18, 23, 15, 15, 4, 13, 15, 13, 5, 14, 20]

julia> t.is_tokenised
true
```
