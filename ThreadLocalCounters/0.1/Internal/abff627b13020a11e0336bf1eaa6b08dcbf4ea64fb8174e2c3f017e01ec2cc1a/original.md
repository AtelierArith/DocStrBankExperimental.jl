```
@tlc [name]
```

Count the time this expression is evaluated using thread-local counters.

# Examples

```jldoctest
julia> using ThreadLocalCounters

julia> hello_world() = @tlc hello_world;
```
