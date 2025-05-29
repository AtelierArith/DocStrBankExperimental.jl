```
when(f, condition::Signal, args...; v0 = nothing)
```

Create a `Signal` that will update to `f(args...)` when any of its input `args` updates *only if* `condition` has value `true`. If `condition != true` in the time of creation the signal will be initialized to value `v0`.

# Examples

```
julia> A = Signal(1)
julia> condition = Signal(A) do a
           a<10
       end
julia> B = when(condition,A) do a
       println("$a is smaller than 10")
   end
julia> A(1)
1 is smaller than 10
1

julia> A(12)
12
```
