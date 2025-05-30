```
@only_one begin ... end
```

これは `@tasks for ... end` ブロック内で使用され、並列タスクのうちの1つだけが実行するコードの領域をマークするために使用されます（他のすべてのタスクはこの領域をスキップします）。

## 例

```julia
using OhMyThreads: @tasks

@tasks for i in 1:10
    @set ntasks = 10

    println(i, ": before")
    @only_one begin
        println(i, ": only printed by a single task")
        sleep(1)
    end
    println(i, ": after")
end
```
