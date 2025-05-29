```
DistributedObject{T}() where T
```

Create an empty `DistributedObject` which will reference objects of type `<:T` stored on remote processes.

For example, `DistributedObject{Int64}()`, will return a distributed object capable of referencing `Int64` objects.

```
DistributedObject{T}(f::Function; pids=workers()::Vector{Int64})
```

Make a reference to objects of type `<:T` stored on processes `pids`. `f` is a function that when executed on a `pid` in `pids` must return an implementation of an object of type `<:T`. The default `pids` are the worker processes.

For example, `DistributedObject((pid)->pid * ones(2); pids=[2,3])`, will return a distributed object referencing a vector `[2,2]` and `[3,3]` stored on workers 2 and 3 respectively.

```
DistributedObject{T}(f::Function, pid::Int64)
```

Make a reference to an object of type `<:T` stored on process `pid`. `f` is a function that when executed on `pid` must return an implementation of an object of type `<:T`.

For example, `DistributedObject(()->ones(2), 4)`, will return a distributed object referencing a vector `[1,1]` stored on workers 4.
