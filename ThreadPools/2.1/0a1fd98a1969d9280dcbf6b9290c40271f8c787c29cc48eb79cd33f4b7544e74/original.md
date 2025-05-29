```
poolresults(pool::QueuePool) -> result iterator
```

Returns an iterator over the `fetch`ed results of the pooled tasks.

# Example

```julia
julia> pool = QueuePool();

julia> @async begin
         for i in 1:4
           put!(pool, x -> 2*x, i)
         end
         close(pool)
       end;

julia> for r in poolresults(pool)
         println(r)
       end
6
2
4
8
```

Note that the execution order across the threads is not guaranteed.
