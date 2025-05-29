```
Mixed(; left = nothing, right = nothing, bottom = nothing, top = nothing)
```

異なる動作を持つ `Mixed` AlignMode を構築します。`nothing` の引数は、その側のバウンディングボックスからの突出を除外します。実数の引数は、その量だけパディングされ、その側のバウンディングボックスからの突出を含みます。`Protrusion` の引数は、固定値で突出を上書きします。
