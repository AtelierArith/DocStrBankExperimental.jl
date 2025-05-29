```
stem(cmd0::String="", arg1=nothing; kwargs...)
```

Example:

```
Y = linspace(-2*pi,2*pi,50);
stem([Y Y], show=true)

stem(Y,[Y -Y], multicol=true, fill=true, show=true)
```
