```
variables(problem::AbstractProblem) -> Vector
```

計算問題における自由度。例えば、最大独立集合問題の場合、それらは頂点のインデックス：1, 2, 3... であり、最大カット問題の場合、それらは辺です。
