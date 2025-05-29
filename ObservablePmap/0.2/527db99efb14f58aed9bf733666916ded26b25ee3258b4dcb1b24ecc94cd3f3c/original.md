```
summary, task = opmap(f, [::AbstractWorkerPool], c...;
                      schedule_now=true, summarize=default_summarize,
                      kwargs... )
```

Transform collection(s) `c` by applying `f` to each element using available workers and tasks, by calling `Distributed.pmap`. The function `f` receives as its first argument a callable `setmessage`, and may call `setmessaage(msg)` to set a status message describing the worker's current status. The returned `summary` is an `Observable` containing a summary string of all workers' statuses including their status messages. The summary may be customized by setting the `summarize` keyword argument.

The application of `f` across available workers is performed asynchronously in the returned `task::Task`. Setting `schedule_now=false` prevents `opmap` from scheduling the task.

The `ObservablePmap` module must be loaded on all workers before calling `opmap`, e.g. by `@everywhere using ObservablePmap`.

Other positional and keyword arguments to `opmap` are the same as for `pmap`.

Example:

```jldoctest
@everywhere using ObservablePmap
using Observables # for `map` method below
summ, task = opmap(1:5; on_error=identity) do setmessage, x
    for i=1:5
        setmessage("$i @ $x")
        (10i+x==33) && error("Error at $i")
        sleep(rand())
    end
end
html = map(x -> HTML("<pre>$x</pre>"), summ)
```
