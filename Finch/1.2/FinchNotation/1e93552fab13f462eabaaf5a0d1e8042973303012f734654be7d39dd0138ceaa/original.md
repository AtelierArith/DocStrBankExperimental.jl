```
initwrite(z)(a, b)
```

`initwrite(z)` is a function which may assert that `a` [`isequal`](https://docs.julialang.org/en/v1/base/base/#Base.isequal) to `z`, and `returns`b`.  By default,`lhs[] = rhs`is equivalent to`lhs[] <<initwrite(fill_value(lhs))>>= rhs`.
