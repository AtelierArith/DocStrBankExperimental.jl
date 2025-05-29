```
@tspawnat tid -> task
```

`Base.Threads.@spawn`を模倣しますが、タスクをスレッド`tid`に割り当てます。

# 例

```julia
julia> t = @tspawnat 4 Threads.threadid()
Task (runnable) @0x0000000010743c70

julia> fetch(t)
4
```
