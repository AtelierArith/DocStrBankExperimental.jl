```
@derefmethod
```

参照型で動作するメソッドを作成するためのマクロで、呼び出しの最初の引数である `x` に対して `deref(x)` へのラッパー呼び出しを生成します。例:

```
@derefmethod foo(x::SectionRef)
```

次のコードが生成されます:

```
foo(x::SectionRef, args...) = foo(deref(x), args...)
```
