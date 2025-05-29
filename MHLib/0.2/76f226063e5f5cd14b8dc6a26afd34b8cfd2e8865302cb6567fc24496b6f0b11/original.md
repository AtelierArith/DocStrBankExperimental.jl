```
destroy!(sol::OneMaxSolution, k::Int, result::Result)
```

`MHMethod` that destroys `k` bits in the solution `sol` by calling `shaking!`.

Note that this is not really a meaningful destroy operation for the OneMax problem. It is just for testing purposes to be able to use the (A)LNS on this problem.
