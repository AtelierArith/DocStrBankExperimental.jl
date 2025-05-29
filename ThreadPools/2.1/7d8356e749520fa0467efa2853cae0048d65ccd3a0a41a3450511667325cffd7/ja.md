```
@logqthreads -> プール
```

`Base.Threads.@threads`を模倣しますが、タスクキュー戦略を使用し、前のタスク（任意のスレッド上）が完了したときにのみ新しいタスクを開始します。ログされたプールを返し、ログ関数や`plot`で分析できます。プライマリスレッドが使用されます。プライマリスレッドの使用を防ぐには、[`@logqbthreads`](@ref)を参照してください。

# 例

```julia
julia> pool = @logqthreads for x in 1:8
         println((x, Threads.threadid()))
       end;
(1, 1)
(3, 2)
(7, 4)
(5, 3)
(2, 1)
(8, 4)
(6, 3)
(4, 2)

julia> plot(pool)
```

実行順序は保証されておらず、プライマリスレッドが使用されることに注意してください。
