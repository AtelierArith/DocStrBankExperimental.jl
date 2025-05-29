```
unfix(context::AbstractContext, syms...)
```

`context`を返しますが、`syms`はもはや固定されていません。

これは再帰的にコンテキストを traverses し、すべての途中で固定を解除します。

関連情報: [`fix`](@ref)
