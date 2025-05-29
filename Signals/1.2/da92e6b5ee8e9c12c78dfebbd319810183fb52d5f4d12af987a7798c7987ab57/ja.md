```
recursion_free(f::Function,args...)
```

は、アクション `f(args...)` が無限ループの再帰から保護された `Signal` を作成します。

```
julia> A = Signal(1)
julia> B = recursion_free(A) do a
            A(a+1)
       end

julia> A(10)
10
julia> A[]
11
```

上記の例では、`recursion_free` を通常の `Signal` に置き換えると、非非同期モードで無限ループが発生します。`recursion_free` はそれを防ぎます。
