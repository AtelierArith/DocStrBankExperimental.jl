```
 s = for_signal(f::Function, range, args...; fps = 1)
```

Create a `Signal` that updates to `f(i,args....) for i in range` every `1/fps` seconds. `range` and `args` can be of type `Signal` or any other type. The loop starts whenever one of the arguments updates. If the previous for loop did not complete it gets cancelled.

# Example

```
rng = Signal(1:5)
A = Signal(2)
B = for_signal(rng,A;fps = 30) do i,a
    println(a^i)
end;
```
