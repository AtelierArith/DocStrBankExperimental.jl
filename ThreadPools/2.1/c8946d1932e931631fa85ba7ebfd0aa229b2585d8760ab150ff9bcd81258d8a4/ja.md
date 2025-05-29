```
@logqbthreads -> プール
```

`Base.Threads.@threads`を模倣しますが、タスクキュー戦略を使用し、前のタスク（任意のスレッド上）が完了したときにのみ新しいタスクを開始します。ログされたプールを返し、ログ関数や`plot`で分析できます。プライマリスレッドは使用されません。プライマリスレッドの使用を許可するには、[`@logqthreads`](@ref)を参照してください。

# 例

```julia
julia> pool = @logqbthreads for x in 1:8
         println((x, Threads.threadid()))
       end;
(2, 3)
(1, 4)
(3, 2)
(4, 3)
(5, 4)
(6, 2)
(7, 3)
(8, 4)

julia> plot(pool)
```

実行順序は保証されませんが、プライマリスレッドはどのジョブにも表示されません。
