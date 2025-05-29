```
replicate!(agent::AbstractAgent model; kwargs...)
```

与えられたエージェントのフィールドの値をコピーして、`model` に新しいエージェントを追加します。`kwargs` を使用すると、`pos` フィールドを含むいくつかのフィールドの新しい値を指定することで、値を上書きすることができます。`id` フィールドは自動的に新しいものに設定されます。

新しいエージェントインスタンスを返します。

## 例

```julia
using Agents
@agent struct A(GridAgent{2})
    k::Float64
    w::Float64
end

model = StandardABM(A, GridSpace((5, 5)))
a = A(1, (2, 2), 0.5, 0.5)
b = replicate!(a, model; w = 0.8)
```
