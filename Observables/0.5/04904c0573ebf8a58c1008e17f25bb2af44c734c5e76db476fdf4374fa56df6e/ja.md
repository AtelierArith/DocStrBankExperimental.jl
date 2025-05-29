```
onany(f, args...; weak::Bool = false, priority::Int = 0, update::Bool = false)
```

`args`にある任意のobservable refsの更新時に`f`を呼び出します。`args`には任意の数の`Observable`オブジェクトを含めることができます。`f`には、refsに含まれる値がそれぞれの引数として渡されます。`args`内の他のオブジェクトはそのまま渡されます。

関連情報: [`on`](@ref).
