```
decondition(context::AbstractContext, syms...)
```

`context`を返しますが、`syms`はもはや条件付けされていません。

これは再帰的にコンテキストを traverses し、途中で全ての条件付けを解除します。

参照: [`condition`](@ref)
