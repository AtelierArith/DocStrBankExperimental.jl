```
    PartialFun(f, args...; kws...)
```

指定された引数で `f` を呼び出す部分適用関数を構築します。未入力の引数を指定するには、`UnfixedArg(T)` または `UnfixedArgSplat(T)` を使用します。ここで、`T` は未入力の引数が取る型を主張します。型の主張を避けるには、`UnfixedArg()` または `UnfixedArgSplat()` を使用します。

例:

```
julia> f = PartialFun(+, 1, UnfixedArg())
+(1, _)

julia> f(2)
3
```
