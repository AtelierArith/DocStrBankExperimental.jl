```
initwrite(z)(a, b)
```

`initwrite(z)`は、`a`が`z`と[`isequal`](https://docs.julialang.org/en/v1/base/base/#Base.isequal)であることを主張する可能性がある関数で、`b`を返します。デフォルトでは、`lhs[] = rhs`は`lhs[] <<initwrite(fill_value(lhs))>>= rhs`と同等です。
