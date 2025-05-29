```
is_mandatory(question::Question)
```

[`Question`](@ref) が必須かどうかを確認します。

# 例

```julia-repl
julia> q = short_text_question("q1", "A question")
julia> is_mandatory(q)
false
```

```julia-repl
julia> q = short_text_question("q1", "A mandatory question", mandatory=true)
julia> is_mandatory(q)
true
```
