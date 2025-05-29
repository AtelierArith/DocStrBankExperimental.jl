```
survey(id, title::String; children, settings)
```

単一言語の [`Survey`](@ref) を構築します。`children` はオプションのキーワード引数であり、省略可能です。

# 例

## 子供なしの調査

```julia-repl
julia> s = survey(100000, "my survey")
Survey with 0 groups and 0 questions.
my survey (id: 100000)

```

## 子供ありの調査

```julia-repl
julia> s = survey(100000, "my survey", children = [
    question_group(1, "first question group"),
    question_group(2, "second question group")
])
Survey with 2 groups and 0 questions.
my survey (id: 100000)
├── first question group (id: 1)
└── second question group (id: 2)
```
