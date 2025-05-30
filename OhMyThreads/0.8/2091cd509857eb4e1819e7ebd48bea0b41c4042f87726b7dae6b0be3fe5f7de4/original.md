```
@one_by_one begin ... end
```

This can be used inside a `@tasks for ... end` block to mark a region of code to be executed by one parallel task at a time (i.e. exclusive access). The order may be arbitrary and non-deterministic.

## Example

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
