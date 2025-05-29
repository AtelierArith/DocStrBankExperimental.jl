```
@logbthreads -> プール
```

`Base.Threads.@threads`を模倣しますが、プライマリスレッドの場合は反復タスクをオフにします。ログを記録したプールを返し、ログ関数や`plot`で分析できます。

# 例

```julia
julia> pool = @logbthreads for x in 1:8
         println((x, Threads.threadid()))
       end;
(3, 4)
(2, 3)
(1, 2)
(4, 4)
(5, 3)
(6, 2)
(8, 3)
(7, 4)

julia> plot(pool)
```

実行順序は保証されていませんが、プライマリスレッドはどのジョブにも表示されません。
