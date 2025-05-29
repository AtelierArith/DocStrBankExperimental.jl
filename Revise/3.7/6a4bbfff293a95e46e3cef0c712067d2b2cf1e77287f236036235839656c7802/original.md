```
revise(mod::Module; force::Bool=true)
```

Revise all files that define `mod`.

If `force=true`, reevaluate every definition in `mod`, whether it was changed or not. This is useful to propagate an updated macro definition, or to force recompiling generated functions. Be warned, however, that this invalidates all the compiled code in your session that depends on `mod`, and can lead to long recompilation times.
