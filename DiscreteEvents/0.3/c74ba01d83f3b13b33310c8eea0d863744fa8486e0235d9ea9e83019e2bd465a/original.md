```
Resource{T}(capacity)
```

A Resource implements a [`Deque`](https://juliacollections.github.io/DataStructures.jl/latest/deque/) with a limited capacity. If used in multithreading applications, the user must avoid race conditions by explicitly wrapping modifying calls with `lock-unlock`.

# Fields

  * `items::Deque{T}`: resource buffer
  * `capacity::Number=Inf`: the capacity is limited to the given integer,
  * `lock::ReentrantLock`: a lock for coordinating resource access by tasks.

# Example

```jldoctest
julia> 
```

!!! note
    In order to use the full interface to `Resource` you have to load `DataStructures`.

