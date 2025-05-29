```
infiltrate(mod, locals, file, line)
```

Function form of `@infiltrate`. Use this to conditionally infiltrate package code without using e.g. Revise (because this version is valid during precompilation).

This would typically be used as

```julia
if isdefined(Main, :Infiltrator)
  Main.infiltrate(@__MODULE__, Base.@locals, @__FILE__, @__LINE__)
end
```
