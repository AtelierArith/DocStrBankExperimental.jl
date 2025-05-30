```
@only_one begin ... end
```

This can be used inside a `@tasks for ... end` block to mark a region of code to be executed by only one of the parallel tasks (all other tasks skip over this region).

## Example

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
