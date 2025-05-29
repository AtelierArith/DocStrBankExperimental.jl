```
submit!(job::Job)
submit!(args_of_Job...; kwargs_of_Job...)
```

Submit the job to queue. 

> `submit!(Job(...))` can be simplified to `submit!(...)`. They are equivalent.


See also [`Job`](@ref), [`@submit`](@ref)
