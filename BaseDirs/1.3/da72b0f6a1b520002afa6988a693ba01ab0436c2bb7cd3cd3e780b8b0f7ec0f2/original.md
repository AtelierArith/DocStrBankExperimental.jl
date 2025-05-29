```
@promise_no_assign expr
```

Evaluate `expr`, while promising that none of the results of `BaseDirs` will be assigned to any global constants.

This macro is intended for use in other package's precompilation scripts, to suppress the spurious warnings about global constant assignments. It will itself warn when used outside precompilation.

# Examples

Within a precompilation workload:

```julia
BaseDirs.@promise_no_assign MyPkg.somecall()
```

Alternatively, you could mark a larger block as safe with `begin ... end`:

```julia
BaseDirs.@promise_no_assign begin
    ...
    MyPkg.somecall()
    ...
end
```
