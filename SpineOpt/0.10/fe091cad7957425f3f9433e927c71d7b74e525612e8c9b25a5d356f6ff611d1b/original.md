```
run_spineopt(f, url_in, url_out; <keyword arguments>)
```

Same as `run_spineopt(url_in, url_out; kwargs...)` but call function `f` with the SpineOpt model as argument right after its creation (but before building and solving it).

This is intended to be called using do block syntax.

```julia
run_spineopt(url_in, url_out) do m
    # Do something with m after its creation
end  # Building and solving begins after quiting this block
```
