```
solve(i::CombinatorialInstance, algo::CombinatorialAlgorithm)
```

Solve the given combinatorial instance `i` using the provided algorithm `algo` (potentially containing parameters for the solving process). The  returned value is a `CombinatorialSolution`. 

If the requested algorithm is not available for this type of instance,  a `MethodError` is thrown.
