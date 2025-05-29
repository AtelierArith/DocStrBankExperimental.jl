```
NLLSsolver.printoutcallback(cost, problem, data, iteratedata)
```

A callback that prints out cost, change in cost and step size each optimization iteration.

# Example

Optimizing an NLLSsolver problem as follows:

```julia
    NLLSsolver.optimize!(problem, options, unfixed, printoutcallback)
```

will cause per iteration information to print out in the terminal.

!!! note
    This callback is useful for debugging, but will incur a performance penalty.

