```
invokelatest(f, args...; kwargs...)
```

`f(args...; kwargs...)`を呼び出しますが、`f`の最も最近のメソッドが実行されることを保証します。これは、古いバージョンの関数`f`を呼び出す可能性のある長時間実行されるイベントループやコールバック関数など、特定の状況で便利です。（欠点は、`invokelatest`は`f`を直接呼び出すよりも若干遅く、結果の型をコンパイラが推論できないことです。）

!!! compat "Julia 1.9"
    Julia 1.9以前では、この関数はエクスポートされておらず、`Base.invokelatest`として呼び出されていました。

