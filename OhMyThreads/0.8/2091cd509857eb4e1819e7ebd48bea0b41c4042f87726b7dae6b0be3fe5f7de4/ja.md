```
@one_by_one begin ... end
```

これは、`@tasks for ... end` ブロック内で使用して、1つの並列タスクによって1回に実行されるコードの領域をマークするために使用できます（つまり、排他的アクセス）。順序は任意で非決定的である可能性があります。

## 例

```julia
using OhMyThreads: @tasks

@tasks for i in 1:10
    @set ntasks = 10

    println(i, ": before")
    @one_by_one begin
        println(i, ": one task at a time")
        sleep(0.5)
    end
    println(i, ": after")
end
```
