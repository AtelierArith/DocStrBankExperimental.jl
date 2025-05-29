Wraps a `Task` with the current cell. When the cell state is reset, sends an `InterruptException` to the underlying `Task`.

```julia
@use_task([]) do
	while true
		sleep(2.)
		@info "this is updating"
	end
end
```

It can be combined with `@use_state` for background updating of values.

I'm still wondering if it is best to have `deps=nothing` as a default, or have `deps=[]` or maybe even require deps explicitly so people are forced to know what they are doing.
