```
summary, task = ologpmap(f, [::AbstractWorkerPool], c...;
                      logger_f=SimpleLogger, schedule_now=true,
                      summarize=default_summarize,
                      kwargs... )
```

Transform collection(s) `c` by applying `f` to each element using available workers and tasks, by calling `Distributed.pmap`. The returned `summary` is an `Observable` containing a summary string of each worker's last log message (emitted by each worker using the `Logging` interface). The keyword argument `logger_f` is invoked with an `IOBuffer` internal to each worker to create a logger writing messages to this buffer. Log message read from this buffer are used as the worker's current status message included in the observable `summary`.

The summary may be customized by setting the `summarize` keyword argument.

The `ObservablePmap` module must be loaded on all workers before calling `ologpmap`, e.g. by `@everywhere using ObservablePmap`.

Other positional and keyword arguments to `ologpmap` are the same as for `opmap`.

Example:

```jldoctest
@everywhere using ObservablePmap
@everywhere using ProgressLogging
@everywhere using TerminalLoggers
summ, task = ologpmap( 'a':'e', 2:2:10;
                       on_error=identity, logger_f=TerminalLogger ) do c, x
    @withprogress name="processing '$c'" for i=1:x
        sleep(rand())
        @logprogress i/x
    end
    @info "finished '$c'"
    x
end
html = map(x -> HTML("<pre>$x</pre>"), summ)
```
