```
@onthreads threadsel expr
```

Execute code in `expr` in parallel on the threads in `threadsel`.

`threadsel` should be a single thread-ID or a range (or array) of thread-ids. If `threadsel == Base.Threads.threadid()`, `expr` is run on the current tread with only minimal overhead.

Example 1:

```juliaexpr
tlsum = ThreadLocal(0.0)
data = rand(100)
@onthreads allthreads() begin
    tlsum[] = sum(workpart(data, allthreads(), Base.Threads.threadid()))
end
sum(getallvalues(tlsum)) ≈ sum(data)
```

Example 2:

```julia
# Assuming 4 threads:
tl = ThreadLocal(42)
threadsel = 2:3
@onthreads threadsel begin
    tl[] = Base.Threads.threadid()
end
getallvalues(tl)[threadsel] == [2, 3]
getallvalues(tl)[[1,4]] == [42, 42]
```
