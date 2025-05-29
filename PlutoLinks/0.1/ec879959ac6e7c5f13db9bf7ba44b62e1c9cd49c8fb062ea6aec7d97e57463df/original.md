Run a code block using debounce, i.e. only run it when variable list has stabilized through `timeout`.

```julia
@use_debounce([var], 1) do
	sleep(2.)
	@info "stable variable $var"
end
```
