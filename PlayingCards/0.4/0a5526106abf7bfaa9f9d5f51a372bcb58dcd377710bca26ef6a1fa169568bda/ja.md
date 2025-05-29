```
low_value(::Card)
low_value(::Rank)
```

低いランクの値。例えば：

  * `Rank(1)` -> 1 (高いエースの値には [`high_value`](@ref) を使用してください。)
  * `Rank(5)` -> 5
