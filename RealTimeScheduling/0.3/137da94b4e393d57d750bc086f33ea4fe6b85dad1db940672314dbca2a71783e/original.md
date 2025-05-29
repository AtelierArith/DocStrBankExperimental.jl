```
schedulable_fixed_priority(T)
```

Check if the [`AbstractRealTimeTaskSystem`](@ref) `T` is schedulable by a fixed priority scheduler, with tasks prioritized by index (low to high).

# Examples

Lehoczky's counterexample to use of traditional TDA when deadlines exceed periods:

```jldoctest lehoczky
julia> ts = TaskSystem([PeriodicTask(70, 70, 26), PeriodicTask(100, 118, 62)]);

julia> schedulable_fixed_priority(ts)
true
```

Shortening the deadline of task 2 makes the system unschedulable:

```jldoctest lehoczky
julia> ts[2] = PeriodicTask(100, 116, 62);

julia> schedulable_fixed_priority(ts)
false
```
