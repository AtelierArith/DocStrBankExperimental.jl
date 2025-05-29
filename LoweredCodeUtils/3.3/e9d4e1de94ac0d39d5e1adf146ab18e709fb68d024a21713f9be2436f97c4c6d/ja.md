```
selective_eval_fromstart!([interp::Interpreter=RecursiveInterpreter()], frame, isrequired, istoplevel=false)
```

[`selective_eval!`](@ref) と同様ですが、`frame.pc` を `isrequired` の最初の `true` ステートメントに設定します。
