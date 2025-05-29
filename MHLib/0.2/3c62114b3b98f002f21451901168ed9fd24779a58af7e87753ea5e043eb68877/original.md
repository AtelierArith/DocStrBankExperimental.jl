```
repair!(sol::OneMaxSolution, ::Nothing, result::Result)
```

`MHMethod` that "repairs" one bit in the solution `sol` by calling `shaking!`.

Note that this is not really a meaningful repair operation for the OneMax problem. It is just for testing purposes to be able to use the (A)LNS on this problem.
