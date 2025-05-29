```
Step{T, S<:Integer}(start, decay, step_sizes)
Step(; start, decay, step_sizes)
```

ステップスケジュールは、`step_sizes`の各ステップごとに`decay`によって指数関数的に減衰します。出力は次の式に従います。

```text
start * decay^{i - 1}
```

ここで、`sum(step_sizes[1:(i - 1)]) < t <= sum(step_sizes[1:i])`です。

# 引数

  * `start`: 開始値
  * `decay`: 減衰率
  * `step_sizes::Union{<:Integer, <:Vector}`: ステップサイズ
