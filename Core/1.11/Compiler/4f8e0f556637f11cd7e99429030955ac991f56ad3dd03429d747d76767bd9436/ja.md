```
already_inferred_quick_test(::AbstractInterpreter, ::MethodInstance)
```

`NativeInterpreter`の場合、何かがすでに推論されたかどうかを知るために実際のキャッシュクエリを行う必要はありません。このポイントに達した場合、推論フラグがオフになっているなら、それはキャッシュにあります。これは純粋にパフォーマンスの最適化のためです。
