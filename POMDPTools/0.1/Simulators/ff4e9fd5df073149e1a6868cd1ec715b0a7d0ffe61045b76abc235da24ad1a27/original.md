```
run(queue::Vector{Sim})
run(f::Function, queue::Vector{Sim})
```

Run the `Sim` objects in `queue` on a single process and return the results as a dataframe.

See `run_parallel` for more information.
