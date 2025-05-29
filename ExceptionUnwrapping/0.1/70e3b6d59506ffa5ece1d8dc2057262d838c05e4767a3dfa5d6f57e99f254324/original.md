```
summarize_current_exceptions(
    io::IO = Base.stderr,
    task = current_task(),
    show_fn = Base.showerror,
)
```

Print a summary of the [current] task's exceptions to `io`. Custom implementations of `Base.showerror` can be passed in as `show_fn`.

This is particularly helpful in cases where the exception stack is large, the backtraces are large, and CompositeExceptions with multiple parts are involved. Custom implementations of `Base.showerror` can be used to control formatting and content of the exception summary.
