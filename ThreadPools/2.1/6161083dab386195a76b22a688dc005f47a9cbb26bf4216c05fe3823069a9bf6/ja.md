```
@logthreads -> プール
```

`Base.Threads.@threads`を模倣します。ロギング関数と`plot`で分析できるログ付きプールを返します。

# 例

```julia
julia> pool = @logthreads for x in 1:8
         println((x, Threads.threadid()))
       end;
(1, 1)
(5, 3)
(7, 4)
(2, 1)
(6, 3)
(8, 4)
(3, 2)
(4, 2)

julia> plot(pool)
```

実行順序は保証されておらず、プライマリスレッドが使用されることに注意してください。
