```
@tspawnat tid -> task
```

Mimics `Base.Threads.@spawn`, but assigns the task to thread `tid`.

# Example

```julia
julia> t = @tspawnat 4 Threads.threadid()
Task (runnable) @0x0000000010743c70

julia> fetch(t)
4
```
