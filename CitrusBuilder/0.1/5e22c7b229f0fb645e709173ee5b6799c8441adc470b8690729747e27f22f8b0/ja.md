```
has_subquestions(question::Question)
```

[`Question`](@ref) にサブ質問があるかどうかを確認します。

# 例

```julia-repl
julia> q = short_text_question("q1", "A question")
julia> has_subquestions(q)
false
```

```julia-repl
julia> q = multiple_short_text_question("q1", "Multiple questions") do
    subquestion("sq1", "subquestion 1"),
    subquestion("sq2", "subquestion 2")
end
julia> has_subquestions(q)
true
```
