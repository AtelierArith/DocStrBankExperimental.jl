```
centralmoment(n, g, args...; kwargs) -> [n by 1 Array]
```

Computes the n central moments of the function g using the Koopman expectation. The function is a wrapper over expectation, arguments can be piped through with args and kwargs.

Return: n-length array of the 1 to n central moments

Note: The first central moment is, by definition, always 0

TODO: - add support for vector-valued g functions, currently assumes scalar        return values.       - add tests
