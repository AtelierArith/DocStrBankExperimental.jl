```
@floop begin
    s₁ = initialization of s₁
    s₂  # pre-initialized variable
    ...
    for x in xs, ...
        ...
    end
end
```

`@floop begin ... end` expects a (possibly empty) series of assignments or variable declaration (as in `s₂` above) followed by a `for` loop.

When there is no induction variables, `begin ... end` can be omitted:

```
@floop for x in xs, ...
    ...
end
```

Use [`@reduce`](@ref) for parallel execution:

```
@floop for x in xs, ...
    ...
    @reduce ...
end
```

`@floop` can also take an `executor` argument (which should be an instance of executor such as `SequentialEx`, `ThreadedEx` and `DistributedEx`) or a `nothing` (indicating an appropriate parallel executor):

```
@floop executor for x in xs, ...
    ...
    @reduce ...
end
```

See the module docstring of [`FLoops`](@ref) for examples.
