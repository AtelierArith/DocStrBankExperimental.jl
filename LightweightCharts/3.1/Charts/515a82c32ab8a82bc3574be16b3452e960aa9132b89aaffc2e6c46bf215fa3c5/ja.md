```
lwc_bar(arg...; kw...) -> LWCChart
```

渡された `arg` から対応するローソク足の値を説明する [`LWCChart`](@ref) を作成します。

## 引数

  * `timestamps::Vector{Union{Real,TimeType}}`
  * `open::Vector{Real}`
  * `high::Vector{Real}`
  * `low::Vector{Real}`
  * `close::Vector{Real}`
