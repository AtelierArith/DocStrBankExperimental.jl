```
with_terminal(f::Function; color::Bool=true, show_value::Bool=true)
```

Run the function, and capture all messages to `stdout`. The result will be a small terminal displaying the captured text.

This allows you to to see the messages from `println`, `dump`, `Pkg.status`, etc.

Example:

```julia
with_terminal() do
    x=1+1
    println(x)
    @warn "Oopsie!"
end 
```

```julia
with_terminal(show_value=false) do
    @time x=sum(1:100000)
end 
```

```julia
with_terminal(dump, [1,2,[3,4]])
```

See also [PlutoUI.Dump](@ref).
