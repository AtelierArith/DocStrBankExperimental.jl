```
high_value(::Card)
high_value(::Rank)
```

高いランクの値。例えば：

  * `Rank(1)` -> 14（低いエースの値には[`low_value`](@ref)を使用してください。）
  * `Rank(5)` -> 5
