```
optimize!(f, search_space, method;logger)
```

Perform an iteration of `method`, and save the results in `method.status`.

### Example

```julia
f, bounds, _ = Metaheuristics.TestProblems.sphere();
method = ECA()
while !Metaheuristics.should_stop(method)
    optimize!(f, bounds, method)
end
result = Metaheuristics.get_result(method)
```

See also [`optimize`](@docs).
