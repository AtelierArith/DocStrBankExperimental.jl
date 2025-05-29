```
(t::TimerOutput)(f, name=string(repr(f))) -> InstrumentedFunction
```

[`TimerOutput`](@ref) `t` によって `f` を計測し、`InstrumentedFunction` を返します。この関数は `f` と同様に使用できますが、呼び出されるたびに `t` にタイミング結果を保存します。
