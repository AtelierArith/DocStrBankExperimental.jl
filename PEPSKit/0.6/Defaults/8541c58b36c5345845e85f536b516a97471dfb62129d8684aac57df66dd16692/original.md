```
set_scheduler!([scheduler]; kwargs...)
```

Set `OhMyThreads` multithreading scheduler parameters.

The function either accepts a `scheduler` as an `OhMyThreads.Scheduler` or as a symbol where the corresponding parameters are specificed as keyword arguments. For instance, a static scheduler that uses four tasks with chunking enabled can be set via

```
set_scheduler!(StaticScheduler(; ntasks=4, chunking=true))
```

or equivalently with 

```
set_scheduler!(:static; ntasks=4, chunking=true)
```

For a detailed description of all schedulers and their keyword arguments consult the [OhMyThreads](https://juliafolds2.github.io/OhMyThreads.jl/stable/refs/api/#OhMyThreads.Schedulers.Scheduler) documentation.

If no `scheduler` is passed and only kwargs are provided, the `DynamicScheduler` constructor is used with the provided kwargs.

To reset the scheduler to its default value, one calls `set_scheduler!` without passing arguments which then uses the default `DynamicScheduler()`. If the number of used threads is just one it falls back to `SerialScheduler()`.
