```
unfix(context::AbstractContext, syms...)
```

`context`を返しますが、`syms`はもはや固定されていません。

これは再帰的にコンテキストを traverses し、途中で全ての固定を解除します。

参照: [`fix`](@ref)
