```
@bthreads
```

`Base.Threads.@threads`を模倣しますが、プライマリスレッドの場合は反復タスクをオフにします。

# 例

```julia
julia> @bthreads for x in 1:8
         println((x, Threads.threadid()))
       end
(1, 2)
(6, 4)
(3, 3)
(7, 4)
(4, 3)
(8, 4)
(5, 3)
(2, 2)
```

実行順序は保証されていませんが、プライマリスレッドはどのジョブにも表示されません。
