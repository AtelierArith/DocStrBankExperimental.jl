```
when(f, condition::Signal, args...; v0 = nothing)
```

`f(args...)` に基づいて更新される `Signal` を作成しますが、これは `condition` が `true` の場合にのみ行われます。作成時に `condition != true` の場合、信号は値 `v0` で初期化されます。

# 例

```
julia> A = Signal(1)
julia> condition = Signal(A) do a
           a<10
       end
julia> B = when(condition,A) do a
       println("$a is smaller than 10")
   end
julia> A(1)
1 is smaller than 10
1

julia> A(12)
12
```
