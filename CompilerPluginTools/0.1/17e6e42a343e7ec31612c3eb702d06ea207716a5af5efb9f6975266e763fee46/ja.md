```
const_invoke!(f, ir::IRCode, ref::GlobalRef)
```

定数である引数 `args` がすべて定数である場合、関数呼び出し `Expr(:invoke, _, ref, args...)` を `f(args...)` に置き換えます。
